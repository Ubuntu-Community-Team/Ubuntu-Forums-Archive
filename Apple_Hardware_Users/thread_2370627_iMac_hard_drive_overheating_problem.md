---
title: "iMac hard drive overheating problem"
date: 2017-09-05
forum: Apple Hardware Users
---

### Post by stefan.jakobsson on 2017-09-05
I've got an iMac mid 2007 20". The hard drive failed recently, and I bought a new one off the shelf and replaced the old one. Since the computer is pretty old, I decided to install ubuntu with gnome desktop. That worked out very nicely, but I soon noticed that the hard drive was overheating. The max operating temperature of the new hard drive is about 54 degrees Celcius.

At least my iMac has three fans: one for the processor, one for the hard drive and one for the optical drive. Even though the hard drive temperature was getting above 55 degrees Celcius, the speed of the hard drive fan would not change.

I solved this with a small C program. The program uses the "hddtemp" package to read the current hard drive temperature.

All necessary configuration is done in the source code:

HDD_TEMP_PATH "hddtemp -n /dev/sda" <= replace /dev/sda if your hard drive has another name
FAN2_MANUAL_PATH "/sys/devices/platform/applesmc.768/fan2_manual" <= If you write a "1" to this file, you get manual control over fan #2, the HDD fan.
FAN2_OUTPUT "/sys/devices/platform/applesmc.768/fan2_output" <= If you have manual control, you may write the requested rpm speed of fan #2 to this file.
FAN_MIN 1250 <= Minimum fan speed (rpm)
FAN_MAX 6000 <= Maximum fan speed

The source code may be compiled with gcc imac-fan.c -o imac-fan.

The application must be run as root.

```

/*

Author: Stefan Jakobsson
License: GPL v 3

Fan controller deamon for iMac mid 2007. The application adjusts speed of fan #2
in order to keep HDD temp within range TEMP_TARGET_LOW to TEMP_TARGET_HIGH.

Depends on hddtemp package, which must be installed separtely. In Debian based
distributions this may be done by:

    sudo apt-get install hddtemp 

*/


#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <signal.h>

#define HDD_TEMP_PATH "hddtemp -n /dev/sda"
#define FAN2_MANUAL_PATH "/sys/devices/platform/applesmc.768/fan2_manual"
#define FAN2_OUTPUT_PATH "/sys/devices/platform/applesmc.768/fan2_output"

#define FAN_MIN 1250
#define FAN_MAX 6000
#define TEMP_TARGET_LOW 45
#define TEMP_TARGET_HIGH 47

int getTemp();
void setFan2Speed(int rpm);
void setFan2Manual(char value[]);
void intHandler(int sig);

static int keepRunning = 1;

int main(){
    //Setup interrupt handler
    signal(SIGINT, intHandler);

    //Take control over HDD fan (fan #2)
    setFan2Manual("1"); 
    
    //Setup starting values
    int prevTemp = 0;
    int currTemp = getTemp();
    int currSpeed;
    if (currTemp < TEMP_TARGET_HIGH){
        currSpeed = FAN_MIN;
    }
    else{
        currSpeed = FAN_MIN+1000;
        if (currSpeed>FAN_MAX) currSpeed=FAN_MAX;
    }
    int targetTemp = TEMP_TARGET_HIGH;
    int coolingPhase = 0;

    setFan2Speed(currSpeed);

    //Loop
    while(keepRunning){
        //Get current temp
        prevTemp = currTemp;
        currTemp = getTemp();

        //Update target temp and cooling phase
        if (coolingPhase && currTemp <= targetTemp){
            targetTemp=TEMP_TARGET_HIGH;
            coolingPhase=0;
        }
        else if (!coolingPhase && currTemp >= targetTemp){
            coolingPhase=1;
            targetTemp=TEMP_TARGET_LOW;
        }

        //Change fan speed if necessary
        if (coolingPhase && currTemp>prevTemp){
            currSpeed+=250;
            if (currSpeed>FAN_MAX) currSpeed=FAN_MAX;
            setFan2Speed(currSpeed);
        }
        else if (!coolingPhase && currTemp<prevTemp){ 
            currSpeed-=250;
            if (currSpeed<FAN_MIN) currSpeed=FAN_MIN;
            setFan2Speed(currSpeed);
        }

        //Output debug info
        printf("Fan speed: %i\nCurrent temp: %i\nPrevious temp: %i\nTarget temp: %i\nPhase: %i\n-----\n", currSpeed, currTemp, prevTemp, targetTemp, coolingPhase);

        //Wait
        sleep(60);
    }

    //Resume kernel fan control
    printf("Resume kernel fan control\n");
    setFan2Manual("0");
    
    return 0;
}

void setFan2Manual(char value[]){
    FILE *fp;
    fp = fopen(FAN2_MANUAL_PATH, "w");
    if (fp==NULL){
        printf("Couldn't change manual fan control mode.");
        return;
    }

    fwrite(value, 1, sizeof(value), fp);
    fclose(fp); 
}

void setFan2Speed(int rpm){
    FILE *fp;
    fp = fopen(FAN2_OUTPUT_PATH, "w");
    if (fp==NULL){
        printf("Couldn't set fan speed.\n");
        return; 
    }
    char value2[10];
    sprintf(value2, "%i", rpm);
    fwrite(value2, 1, sizeof(value2), fp);
    fclose(fp);
}

int getTemp(){
    FILE *fp;
    char response[256];

    fp = popen(HDD_TEMP_PATH, "r");
    if (fp==NULL){
        printf("Couldn't access hdd temp");
        return -1;
    }
    
    if (fgets(response, sizeof(response)-1, fp)==NULL){
        printf("Couldn't read hdd temp");
        pclose(fp);
        return -1;
    }
    else{
        pclose(fp);
        return atoi(response);
    }
}

void intHandler(int sig){
    signal(sig, SIG_IGN);
    keepRunning = 0;
}

```

---

