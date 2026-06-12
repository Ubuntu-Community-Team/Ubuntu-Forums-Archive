---
title: "Macbook 4,1 - natty - (MACFANCTL) Helpme Please"
date: 2011-05-08
forum: Apple Hardware Users
---

### Post by samuaz on 2011-05-08
Hello beautiful people, I recently installed ubuntu 11.04, in my white macbook 4.1, following the guide https: / / help.ubuntu.com/community/MacBook4-1/Natty, I followed everything to the letter and I have a very good installation of ubuntu on my macbook, but I have two problems:
1. The iSight camera
2. the fan and temperature control, which is what most interests me

install the package: macfanctl, as indicated in the guide, and modify the macfanctl to make it more like osx, my current macfanctl.conf file is:

# Config file for daemon macfanctl
#
# Note: 0 <temp_X_floor <temp_X_ceiling
# 0 <fan_min <6200

fan_min: 2200

temp_avg_floor: 55 # 45
temp_avg_ceiling: 65 # 55

temp_TC0P_floor: 55 # 50
temp_TC0P_ceiling: 65 # 58

temp_TG0P_floor: 55 # 50
temp_TG0P_ceiling: 65 # 58

# Add sensors to Be Excluded here, Separated by space, ie
# Exclude: 1 7
# Will disable reading of sensors temp1_input and temp7_input.

exclude:

# Log_level values:
# 0: Startup / Exit logging only
# 1: Basic temp / fan logging
# 2: Log all sensors

log_level: 2

however it does not work because my macbook fan is always at 6200 rpm while the temperature is 55 degrees Celsius the fan always at full speed, in Macosx the control is much smoother and scalable, for example to 50 - 60 degrees is about normal temperature of the macbook osx is maintained at between 1800-2000 rpm and is scaled according to whether the temperature increases or decreases very rarely put the fan to maximum speed on Macosx, unless you are running a game video or an application that requires it, but ubuntu is always at 6200 rpm even with the installed macfanctl and 54 degrees Celsius, when I run the command: (macfanctld-f), I get different errors, which leads me to think something wrong:

macfanctld-f
Running in foreground, log to stdout.
Using parameters:
temp_avg_floor: 55
temp_avg_ceiling: 65
temp_TC0P_floor: 55
temp_TC0P_ceiling: 65
temp_TG0P_floor: 55
temp_TG0P_ceiling: 65
fan_min: 2200
log_level: 2
Found 1 fan.
Found 10 sensors:
1: TB0T - Battery Temp TS_MAX
2: TC0D - CPU 0 Die Temp
3: TC0P - CPU 0 Temp Proximity
4: TM0P -?
5: TN0P - MCP Proximity
6: TTF0 -?
7: TW0P -?
8: Th0H -?
9: Th0S -?
10: Th1H -?
Error: Can not open / sys/devices/platform/applesmc.768/fan1_min
Error: Can not open / sys/devices/platform/applesmc.768/fan1_manual
Speed: 2200, AVG: 55.2C, TC0P: 54.8C, Sensors: TB0T: 34 TC0D: 57 TC0P: 55 TM0P: 57 TN0P: 54 TTF0: 58 TW0P: 70 Th0H: 56 Th0S: 56 Th1H: 56
Error: Can not open / sys/devices/platform/applesmc.768/fan1_min
Error: Can not open / sys/devices/platform/applesmc.768/fan1_manual
Speed: 2200, AVG: 55.3C, TC0P: 54.8C, Sensors: TB0T: 34 TC0D: 58 TC0P: 55 TM0P: 57 TN0P: 54 TTF0: 58 TW0P: 70 Th0H: 56 Th0S: 56 Th1H: 56
Error: Can not open / sys/devices/platform/applesmc.768/fan1_min
Error: Can not open / sys/devices/platform/applesmc.768/fan1_manual
Speed: 2200, AVG: 55.2C, TC0P: 54.5C, Sensors: TB0T: 34 TC0D: 57 TC0P: 54 TM0P: 57 TN0P: 54 TTF0: 58 TW0P: 70 Th0H: 56 Th0S: 56 Th1H: 56
Error: Can not open / sys/devices/platform/applesmc.768/fan1_min
Error: Can not open / sys/devices/platform/applesmc.768/fan1_manual
Speed: 2200, AVG: 55.2C, TC0P: 54.8C, Sensors: TB0T: 34 TC0D: 57 TC0P: 55 TM0P: 57 TN0P: 54 TTF0: 58 TW0P: 70 Th0H: 56 Th0S: 56 Th1H: 56
Error: Can not open / sys/devices/platform/applesmc.768/fan1_min
Error: Can not open / sys/devices/platform/applesmc.768/fan1_manual
Speed: 2200, AVG: 55.3C, TC0P: 54.8C, Sensors: TB0T: 34 TC0D: 57 TC0P: 55 TM0P: 57 TN0P: 54 TTF0: 58 TW0P: 70 Th0H: 56 Th0S: 56 Th1H: 56
Error: Can not open / sys/devices/platform/applesmc.768/fan1_min
Error: Can not open / sys/devices/platform/applesmc.768/fan1_manual
Speed: 2200, AVG: 55.5C, TC0P: 54.8C, Sensors: TB0T: 34 TC0D: 58 TC0P: 55 TM0P: 57 TN0P: 54 TTF0: 58 TW0P: 70 Th0H: 56 Th0S: 56 Th1H: 56
Error: Can not open / sys/devices/platform/applesmc.768/fan1_min
Error: Can not open / sys/devices/platform/applesmc.768/fan1_manual
Speed: 2200, AVG: 55.5C, TC0P: 54.8C, Sensors: TB0T: 34 TC0D: 57 TC0P: 55 TM0P: 57 TN0P: 54 TTF0: 58 TW0P: 70 Th0H: 56 Th0S: 56 Th1H: 56
Error: Can not open / sys/devices/platform/applesmc.768/fan1_min
Error: Can not open / sys/devices/platform/applesmc.768/fan1_manual
Speed: 2200, AVG: 55.5C, TC0P: 55.0C, Sensors: TB0T: 34 TC0D: 57 TC0P: 55 TM0P: 57 TN0P: 54 TTF0: 58 TW0P: 70 Th0H: 56 Th0S: 56 Th1H: 56
Error: Can not open / sys/devices/platform/applesmc.768/fan1_min
Error: Can not open / sys/devices/platform/applesmc.768/fan1_manual
Speed: 2200, AVG: 55.5C, TC0P: 55.0C, Sensors: TB0T: 34 TC0D: 58 TC0P: 55 TM0P: 57 TN0P: 54 TTF0: 58 TW0P: 70 Th0H: 56 Th0S: 56 Th1H: 56
Error: Can not open / sys/devices/platform/applesmc.768/fan1_min
Error: Can not open / sys/devices/platform/applesmc.768/fan1_manual
Speed: 2200, AVG: 55.6C, TC0P: 55.0C, Sensors: TB0T: 34 TC0D: 58 TC0P: 55 TM0P: 57 TN0P: 54 TTF0: 58 TW0P: 70 Th0H: 56 Th0S: 56 Th1H: 56

so I am given to understand that I have the macfanctl misconfigured or not working correctly.

please, someone could help me to successfully configure the fan in my macbook, to make it smooth and scalable as osx is the only thing that stops me to take the definitive step to leave behind ubuntu and osx

Greetings and thanks in advance

PS: attached a screenshot where the status bar shows the temperature and rpm of the fan

I am a newbie this is my first successful installation of ubuntu please help me!!

---

### Post by Silmathoron on 2011-05-08
I'm not familiar with macfanctl, so I don't really know what could be wrong.
However, you may want to try smcfancontrol, which worked really well for me. The installation should be detailed here [http://ubuntuforums.org/showthread.php?t=1102465&highlight=macbook+smcfancontrol](http://ubuntuforums.org/showthread.php?t=1102465&highlight=macbook+smcfancontrol)

---

### Post by samuaz on 2011-05-08
> **Silmathoron said:**
> I'm not familiar with macfanctl, so I don't really know what could be wrong.
However, you may want to try smcfancontrol, which worked really well for me. The installation should be detailed here [http://ubuntuforums.org/showthread.php?t=1102465&highlight=macbook+smcfancontrol](http://ubuntuforums.org/showthread.php?t=1102465&highlight=macbook+smcfancontrol)

thank you very much I will try it, uninstall the macfancld,

a question after installation, start automatically with the system or I have to start it? and how I can change the options?

thanks greetings

---

### Post by Silmathoron on 2011-05-08
Everything is in the thread and the Readme :
Open the archive, edit smcfancontrol, put the values you want, then enter
```
cd "the directory of smcfancontrol"
sudo ./install
```

Judging by the install file, it should runs automatically on statup... you may ask on the thread

---

### Post by samuaz on 2011-05-08
omg! is great works very very well! Excellent!.

by the way, you carry more time using it, what is your configuration? 
minTemp=?
maxOnlineTemp=?
maxOfflineTemp=?

tempCalc= highest or average?	
sensorsUsed=?		
checkInterval=?	

thank you very much, you are very nice (Y)

---

### Post by Silmathoron on 2011-05-08
Sorry, I'm not using it at the moment, but to sum up, the settings were quite good to me... I think I used "highest" and increased the fanMinSpeed to 2500. If you want to save power, you can increase checkInterval a bit.

---

### Post by samuaz on 2011-05-08
the script has stopped working me again the fans are fired at 6200 rpm and the temperature at 40-45 degrees: S, now you do not know what could have happened, it worked so well, cry cry cry

---

### Post by Silmathoron on 2011-05-09
Did you do anything new ?
Make sure you have "coretemp" in /etc/modules and "sensors-applet" installed...

---

### Post by samuaz on 2011-05-09
yes i have coretemp in /etc/modules and now install sensors-applets, but sometimes it works sometimes not, it seems as if the system is another sensor and avoids the parameters of the script, and starts to handle the fans, I and my fan_manual set to 0, I think that means automatic, I have put in manual mode? as I do?

---

