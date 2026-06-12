---
title: "(how to) tutorial for controlling fan macbook / pro in natty 11.04"
date: 2011-05-10
forum: Apple Hardware Users
---

### Post by samuaz on 2011-05-10
UPDATE 12/01/2012
- updated for orneric and kernel 3.x
- change 
- appldkms its no more need

***TESTED IN A WHITE MACBOOK 4.1 cor2duo

after several reinstalls the system, drivers, scripts and other programs, I could control the fan in my macbook 4.1 in ubuntu natty 11.04

these were always running at full speed 6200 rpm, regardless of whether the temperature was high or low, 40 degrees or 70 degrees, as did the fans are not regulated!

still following the ubuntu help manual for my macbook and installing macfanctl, there was no way to control the fan ...

after doing a million tests and configurations, and listen to advice, I've found it!

the problem is not in control the minimum speed or maximum speed of the fans, what matters is the current speed of the fan and the output speed!.
macfanctld apparently has no option for this and is based solely on the minimum and maximum speed but not control the actual parameter that is running the fan and output speed.

The solution is easy, not as I did not think before!.
Instead of using macfanctl, install the script smcFanControl and set up to control the output speed of the input also! making the actual speed of the fan in my macbook change according to the temperature I want! Excellent!

But my white macbook 4.1, in osx at a temperature of 50-60 degrees the fan is at 1800 rpm, if it rises to 60 increases to 2500-3000 rpm, and reach 70 degrees Celsius or more the speed increases to 6200 rpm the temperature dropping rapidly, temperatures are high but if Apple allows these temperatures so high is because macs support them, and to blame for the high temperatures of the macbooks / pro is not the cpu or gpu is the airport card, being turned on this easily reaches temperatures of 70-80 degrees YES LOL!, but Apple says this is normal operating temperature, so even if the cpu is at 40 degrees and the bottom of the macbook feel this burn, but it is the airport, if airport off temperature drops to 50-60 degrees ..

ok go on with it! first thank the creator of smcFanControl, applesmc-dkms, lm-sensors, sensors-applet-sysmonitor indicator, and the large community of ubuntu, if you have problems with your macbook fans are always at 6200 rpm or want to control them as you like These are the steps to follow (it worked for me):

*** IF YOU HAVE INSTALLED: MACFANCTLD, APPLESMC-DKMS, Uninstall from Terminal:
sudo apt-get purge macfanctld
sudo apt-get purge applesmc-dkms

1. install lm-sensors: sudo apt-get install lm-sensors
2. configure the sensors and add to /etc/modules, in terminal run: sensors-detect, answer yes to all questions, once finished searching all the sensors are sensors cpu will come out and ask them if they want to add them to /etc/modules RESPOND YES
example:
#---- Cut here ----
CoreTemp
LM75 (lm75 can change in your macbook, so use the your its only example)
#---- Cut here ----
ask if you want to automatically add them to /etc/modules, respond YES 

3.According To the sensors found, do a modprobe in the terminal. example:
sudo modprobe coretemp
sudo modprobe lm75 (lm75 can change in your macbook, so use the your its only example)

5.[COLOR="Red"]********** NO MORE NEEDED ON ORNERIC 11.10 ***********[/COLOR] Download applesmc-dkms for natty 11.04 (attached to the post), original link [http://ubuntuforums.org/showthread.php?t=1102465&page=6#59](http://ubuntuforums.org/showthread.php?t=1102465&page=6#59)
unzip the download, and install the .deb from terminal:
cd "folder of the .deb file"
sudo dpkg -i applesmc-dkms_0.17.4-natty-mactel1~test1_all.deb [COLOR="Red"]********** NO MORE NEEDED ON ORNERIC 11.10 ***********[/COLOR]

6. Download smcFanControl for natty and smcfancontrol-orneric for new ubuntu 11.10 (attached to the post), original link: [http://ubuntuforums.org/showthread.php?t=1102465#1](http://ubuntuforums.org/showthread.php?t=1102465#1)

7. unzip the download and configure smcFanControl: OPEN THE FILE: smcFanControl with gedit and configure:

minTemp=		# Lowest temperature ----> Minimum temperature, 55 degrees to my taste, BATTERY SAVING, AND SIMILAR TO PARAMETER USED BY APPLE

maxOnlineTemp=		# Highest temperature when online ----> 65 DEGREES TO MY TASTE

maxOfflineTemp=		# Highest temperature when offline -->  ACCORDING TO YOUR TASTE, BUT APPLE RAISES THE SPEED 6200 RPM WHEN THE TEMPERATURE REACHED 70 DEGREES

fanMinSpeed=2000	# Lowest fan-speed --- ACCORDING TO YOUR TASTE

fanMaxSpeed=6200	# Highest fan-speed ----------> 6000 Change for 6200 most fans of core2duo macbooks, support a speed of 6200 rpm

tempCalc=highest	# Temperature calculation ("highest" uses highest temperature, "average" takes the average, ----> PREFERABLY HIGH, BUT ACCORDING TO YOUR TASTE TEST AVERAGE

sensorsUsed=2		# How many sensors to use (first sensors are for coretemp, one for each CPU core ---->  2 works well

:KS *** manFanControl=false	# Set to true if you want to define direct output, instead of fan minimum speeds --> IMPORTANT CHANGE TO TRUE
IF NOT THE FAN NOT DROP TO 6200 RPM although the temperature is low

useCoretemp=true	# Set to false if you don't want to use coretemp sensors --> no change it

checkInterval=10	# Interval to check whether fan speed needs an update (in seconds) --> according to your tastes, I prefer 1 or 3 seconds to more accurately but spends most battery

updateInterval=0.5  # works very well

save and exit

8. install smcfancontrol from terminal:
cd "smcfancontrol folder"
sudo ./install

9. completely shut down the macbook, turn it on ubuntu start and continue with step 10

10. optional indicator-sysmonitor install, to  monitor the speed and temperature run in terminal:

sudo add-apt-repository ppa:alexeftimie/ppa
sudo apt-get update
sudo apt-get install indicator-sysmonitor

11.to open it: alt + f2 and run indicator-sysmonitor, and configure the sensors to display, should be:
CoreTemp-isa-0000
CoreTemp-isa-0001
Fan exhaust
(CoreTemp, are sensors of the processor, which is based the script for manipulating the fan)

12. enjoy a good control of the fan and temperature according to your taste!

*** SURELY WORKS FOR ALL MacBooks/PRO, TESTED IN A WHITE MACBOOK 4.1

ATTACH PICTURE OF OSX TEMP AND FAN IN LEOPARD 10.5.8 MACBOOK WHITE 4,1 CORE2DUO

GREETINGS ENJOY

---

### Post by Joushou on 2011-05-11
I'm glad to see that people are still finding my script useful! Hah, and I who thought people would scold me for being a n00bish scripter... :P

Oh, and it should work for any Mac supporting the applesmc and coretemp kernel modules, which means all MacBook (Pro)'s, and maybe also iMacs/Mac Mini/Mac Pro's, I don't know, haven't tried... All I know is that I designed it to work with any amount of fans and sensors. (As long as the number of sensors and fans can fit into your RAM...)

---

### Post by samuaz on 2011-05-13
thanks for the script the truth is the best and only thing that worked for me
the possibility of controlling the output speed is amazing xD

there is a chance to make some improvements in how to use script
other sensors such as "CPU DIED" AND PROXIMITY AND TC0D TC0P and the gpu sensor for macbook pro

and different options depending on whether you plugged or
battery, eg battery with minimum speed is 2000
rpm and the power adapter is 3500 for example?

Greetings and thank you very much for the script

---

### Post by Geremia on 2011-05-16
Duplicate: See below.

---

### Post by Geremia on 2011-05-16
Your instructions didn't work for me.

When I ran [FONT=Courier New]sensors-detect[/FONT], at the last step it said that [FONT=Courier New]/etc/modules[/FONT] is deprecated, and so I don't think it wrote the file.

When I ran [FONT=Courier New]sudo apt-get install sensors-applet[/FONT], I told it not to start some daemon on boot. Is that okay?

Lastly, [FONT=Courier New]indicator-sysmonitor[/FONT] returned this:
```
INFO:root:Menu shown
[Errno 2] No such file or directory: '/home/alan/.indicator-sysmonitor.json'
ERROR:root:Reading settings failed
INFO:root:Fetcher started
```

I am on a Macbook 2,1 with Ubuntu 11.04. Thanks

Currently, [FONT=Courier New]sensors[/FONT] says I am running at 6216 RPM! I thought the max was 6200!

---

### Post by samuaz on 2011-05-16
the indicator-sysmonitor does not affect the script, it's just 
visual aid to know the temperature and others .. 
the important thing is to have the CoreTemp in /etc/modules, if having 
made the sensor-detect, it does not add the sensors you add it to the module 
manually, because if the sensors are not in the module, the script 
will have sensors to read the parameters 

sudo gedit /etc/modules 

and add the sensors to the end of the file, enough only to write 
name of the sensors, for my macbook 4.1 are: 

coretemp 
lm75 

this is my /etc/modules 

# /Etc/modules: kernel modules to load at boot time. 
# 
# This file contains the names of kernel modules loaded That Should Be 
# At boot time, one per line. Lines beginning with "#" are ignored. 

lp 
rtc 

# Generated by sensors-detect on Sat May 14 20:34:53 2011 
# Chip drivers 
Coretemp 
lm75 

then modprobe them have a "sudo modprobe coretemp" and "sudo modprobe lm75" 

check whether these are your sensors on your processor, I recommend you do a new sensors-detect 

but I imagine that your macbook are the same sensors coretemp, my macbook, so try adding the /etc/modules 

then if you installed the smcFanControl correctly this should have 
configuration file in the following path: /usr/local/sbin/ smcFanControl 

check it by doing the following 

sudo gedit /usr/local/sbin/smcFanControl 

and check the configuration: manFanControl be true 

you can use my configuration: 

minTemp = 50 
maxOnlineTemp = 60 
maxOfflineTemp = 60 

fanMinSpeed &#8203;&#8203;= 2000 
fanMaxSpeed &#8203;&#8203;= 6200 

tempCalc = Highest 
sensorsUsed = 2 
debug = onChange 
manFanControl = true 
useCoretemp = true 
checkInterval = 1 
UpdateInterval = 0.5 

with this configuration should run you well, assuming that 
previously uninstalled the macfanctld doing an apt-get purge of 
it and installed the applesmc-dkms and the script should run you well adding sensors to the module and the settings you have set 

after doing the above steps in a terminal run 

sudo service smcfancontrol.sh restart 

if you get it has been restarted, the script should respond OK 
already run you, 

if you still run you check the following: 

sensors that are coretemp processor for your macbook and that they are 
loaded in the /etc/modules, if those are not test reinstall the package lm-sensors and sensors-detect do it again and answer YES to all 

if you do not use ubuntu 11.04, the "applesmc-dkms" that you should install is the is in Mactel for your version of ubuntu, 10.10, 10.04 etc. 

reinstall the script to test the settings I have given is 
important option "manFanControl=true", TRUE 

applet-sensors is not necessary, it's just a visual aid not install it if you want 

the indicator-sysmonitor you run it with alt + f2 and write there 
indicator-sysmonitor, if the indicator-sysmonitor, do not receive the "CoreTemp information" is not loaded in /etc/modules is vital that they are loaded in the module 

with this and should run you, tell us what was your 

6216 the speed is normal, remember they are rpm always give a little more, do not worry about it


I recommend you change the cpu governor to conservative, works better than ondemand and makes the processor is not so hot

---

### Post by Geremia on 2011-05-16
> **samuaz said:**
> the indicator-sysmonitor does not affect the script, it's just 
visual aid to know the temperature and others .. 
the important thing is to have the CoreTemp in /etc/modules, if having 
made the sensor-detect, it does not add the sensors you add it to the module 
manually, because if the sensors are not in the module, the script 
will have sensors to read the parameters 

sudo gedit /etc/modules 

and add the sensors to the end of the file, enough only to write 
name of the sensors, for my macbook 4.1 are: 

coretemp 
lm75 

this is my /etc/modules 

# /Etc/modules: kernel modules to load at boot time. 
# 
# This file contains the names of kernel modules loaded That Should Be 
# At boot time, one per line. Lines beginning with "#" are ignored. 

lp 
rtc 

# Generated by sensors-detect on Sat May 14 20:34:53 2011 
# Chip drivers 
Coretemp 
lm75 Mine actually isn't blank; luckily, it says:```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
b44

# Generated by sensors-detect on Sun May 15 21:38:26 2011
# Chip drivers
coretemp

```> **samuaz said:**
> then modprobe them have a "sudo modprobe coretemp" and "sudo modprobe lm75" 

check whether these are your sensors on your processor, I recommend you do a new sensors-detect 

but I imagine that your macbook are the same sensors coretemp, my macbook, so try adding the /etc/modules 

then if you installed the smcFanControl correctly this should have 
configuration file in the following path: /usr/local/sbin/ smcFanControl 

check it by doing the following 

sudo gedit /usr/local/sbin/smcFanControl Mine is /usr/local/sbin/smcfancontrol, but that's pretty much the same.> **samuaz said:**
> and check the configuration: manFanControl be true Yes, it's configured alright. I hear my fan changing speed quite frequently now that I did a second restart. (Apparently, one reboot wasn't enough to get it going, or perhaps it was going, but my machine was so hot that it had to run the fan continuously as before.)> **samuaz said:**
> you can use my configuration: 

minTemp = 50 Why so high for the minTemp? Even with mine set this high, the fan still runs at ~6200 RPM with very little CPU usage. I wonder if there is dust that needs to be vacuumed out that is preventing a good airflow?> **samuaz said:**
> maxOnlineTemp = 60 
maxOfflineTemp = 60 

fanMinSpeed &#8203;&#8203;= 2000 
fanMaxSpeed &#8203;&#8203;= 6200 

tempCalc = Highest 
sensorsUsed = 2 
debug = onChange 
manFanControl = true 
useCoretemp = true 
checkInterval = 1 
UpdateInterval = 0.5 

with this configuration should run you well, assuming that 
previously uninstalled the macfanctld doing an apt-get purge of 
it and installed the applesmc-dkms and the script should run you well adding sensors to the module and the settings you have set 

after doing the above steps in a terminal run 

sudo service smcfancontrol.sh restart 

if you get it has been restarted, the script should respond OK 
already run you, 

if you still run you check the following: 

sensors that are coretemp processor for your macbook and that they are 
loaded in the /etc/modules, if those are not test reinstall the package lm-sensors and sensors-detect do it again and answer YES to all 

if you do not use ubuntu 11.04, the "applesmc-dkms" that you should install is the is in Mactel for your version of ubuntu, 10.10, 10.04 etc. 

reinstall the script to test the settings I have given is 
important option "manFanControl=true", TRUE Yes, it definitely is.> **samuaz said:**
> applet-sensors is not necessary, it's just a visual aid not install it if you want Do you know why it doesn't work for me, though? I guess I could just run [FONT=Courier New]sensors[/FONT].> **samuaz said:**
> the indicator-sysmonitor you run it with alt + f2 and write there 
indicator-sysmonitor, if the indicator-sysmonitor, do not receive the "CoreTemp information" is not loaded in /etc/modules is vital that they are loaded in the module 

with this and should run you, tell us what was your 

6216 the speed is normal, remember they are rpm always give a little more, do not worry about it


I recommend you change the cpu governor to conservative, works better than ondemand and makes the processor is not so hotYes, I usually keep it on powersave, but conservative sounds good, too. Thanks

---

### Post by samuaz on 2011-05-16
I have 50 degrees for the minimum speed setting, since my macbook is never at a lower temperature than that, though the fan is continuously at 6200 rpm, never lower than 49 degrees Celsius 
even in osx, Macosx maintains fan: 1800 rpm 
always and only up to "60-70" puts them at 6200 degrees to lower 
quickly to a standard temperature between 50-60, have shown that 
the script for example: if you put the minimum temperature at 40 degrees my 
Fan always run at high speed for my macbook never at 
that temperature, that is the basis for setting speed 
fan, for example: 50 degrees will be at 2000 rpm at 53 degrees and will be in 2600 and will gradually be increased, if you put the 
minimum speed at 40 degrees when your MacBook is at 50 degrees 
fan is at 4000 rpm, and my macbook is 50-60 degrees 
normal operating temperature, a temperature that keeps mac osx 
the minimum fan speed, so I understand that is the temperature 
normal operation. 

If you already have loaded CoreTemp in / etc / modules / the script and should work for you not because you do not even work: S 

only if previously installed macfanctl tiens a purge to uninstall it by "sudo apt-get purge macfanctld." 

You can run "sensors" in the terminal should give you something like this: 

 samuel @ samuel-MacBook: ~ $ sensors 
applesmc-isa-0300 
Adapter: ISA adapter 
Exhaust: 2001 RPM (min = 1800 RPM) 
TB0T: +32.0 ° C 
TC0D: +53.2 ° C 
TC0P: +51.0 ° C 
TM0P: +49.2 ° C 
TN0P: +50.0 ° C 
TTF0: +65.0 ° C 
TW0P: +56.0 ° C 
Th0H: +52.2 ° C 
Th0S: +52.2 ° C 
Th1H: +52.5 ° C 

CoreTemp-isa-0000 
Adapter: ISA adapter 
Core 0: +45.0 ° C (high = +105.0 ° C, crit = +105.0 ° C) 

CoreTemp-isa-0001 
Adapter: ISA adapter 
Core 1: +45.0 ° C (high = +105.0 ° C, crit = +105.0 ° C) 

these are the temperatures and fan speed, you have my macbook at the moment 

test put the script minimum speed of 50 degrees, save the file, and then restart the script "sudo service smcfancontrol.sh restart" and run "sensors" in terminal and see if your fan speed is down for example if have the minimum temperature at 50 degrees and the maximum to 60, to 55 degrees the fan speed of your mac should be approximately 3100 rpm

---

### Post by japboy on 2011-05-16
I've tried this instruction on my iMac (Intel Core i3 Mid2010 model) and it seems that there's no problem so far. Max fan speed is really noisy though :(
Thanks for great instruction!

---

### Post by japboy on 2011-05-17
Well, I got a problem.

Once fan speed is increased, smcfancontrol never decrease the fan speed :(

Here's the log:


```
$ tail -f /var/log/smcfancontrol.log
...
17/05 15:03:10: Temperature: 24, Fan-speed: 2000, ACPI-State: offline
17/05 15:03:20: Temperature: 23, Fan-speed: 2000, ACPI-State: offline
17/05 15:03:40: Temperature: 31, Fan-speed: 2000, ACPI-State: offline
17/05 15:03:40: FATAL: Failing at: setting fans
17/05 15:03:40: Attempting to set fans to safe values
17/05 15:03:40: Committing suicide. Bye.
```

If I run ```
smccontrol
``` directly again, the fan becomes quiet though.

Any idea to fix this? Thanks in advance.

---

### Post by samuaz on 2011-05-17
perhaps could be that your problem is "ACPI-State: offline"in my macbook this
is online:

samuel @ samuel-MacBook: ~ $ tail-f / var / log / smcfancontrol.log
05/17 7:11:57: Temperature: 49, Fan-speed: 2000, ACPI-State: online
05/17 7:12:09: Temperature: 50, Fan-speed: 2000, ACPI-State: online
05/17 7:12:10: Temperature: 49, Fan-speed: 2000, ACPI-State: online
05/17 7:12:12: Temperature: 50, Fan-speed: 2000, ACPI-State: online
05/17 7:12:19: Temperature: 49, Fan-speed: 2000, ACPI-State: online
05/17 7:12:21: Temperature: 50, Fan-speed: 2000, ACPI-State: online
05/17 7:12:23: Temperature: 49, Fan-speed: 2000, ACPI-State: online
05/17 7:12:28: Temperature: 50, Fan-speed: 2000, ACPI-State: online
05/17 7:12:38: Temperature: 51, Fan-speed: 2420, ACPI-State: online
05/17 7:12:39: Temperature: 50, Fan-speed: 2000, ACPI-State: online

but as you say if you re-start the script the fan back to normal, then something is off script

before installing the script, first uninstall the macfanctl?

to restart the script running in terminal: "sudo service smcfancontrol.sh restart"

check in /usr/local/sbin/smcFanControl that these options are true

sensorsUsed = 2
manFanControl = true
useCoretemp = true

---

### Post by japboy on 2011-05-17
Thanks for reply.

First, I've never tried *macfanctl* so don't have to uninstall anything, right?

Actually, restarting is not really restarting. I just run *smcfancontrol* directly like below:

```
$ sudo /usr/local/sbin/smcfancontrol 
cat: /proc/acpi/battery/BAT0/state: No such file or directory
cat: /proc/acpi/ac_adapter/ADP1/state: No such file or directory
```

Then the *sensors* command shows decresed fan speed around 2000 RPM (noisy speed is around 4000 RPM according to *sensors* command)

```
$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +24.0°C  (high = +89.0°C, crit = +105.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +27.0°C  (high = +89.0°C, crit = +105.0°C)  

applesmc-isa-0300
Adapter: ISA adapter
ODD :       4001 RPM  (min = 4000 RPM)
HDD :       4001 RPM  (min = 4000 RPM)
CPU :       4001 RPM  (min = 4000 RPM)
...
```

```
$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +22.0°C  (high = +89.0°C, crit = +105.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +25.0°C  (high = +89.0°C, crit = +105.0°C)  

applesmc-isa-0300
Adapter: ISA adapter
ODD :       2003 RPM  (min = 4000 RPM)
HDD :       1996 RPM  (min = 4000 RPM)
CPU :       1997 RPM  (min = 4000 RPM)
...
```

BTW, I also checked the fan speed on Mac OS X by [smcFanControl]("http://www.eidac.de/?p=134"), and it shows around 1000 RPM as default. So iMac's *fanMinSpeed* can be 1000, right?

> check in /usr/local/sbin/smcFanControl that these options are true

sensorsUsed = 2
manFanControl = true
useCoretemp = true

Yes, those parameters are same as you mentioned. I haven't changed the default settings, actually.

Additionally, I have a question. Do I really have to install *applesmc-dkms_0.17.4-natty-mactel1~test1_all.deb.gz*? Because I checked *smcfancontrol* behaviour w/ or w/o it, and there seemed to be no difference.

---

### Post by japboy on 2011-05-18
this seems to be caused by changing fan speed, and *smcfancontrol* does hard reset to 4000 RPM when changing failure happens and kills itself... after that, i run *sudo service smcfancontrol.sh start* then fan speed is decreased w/o problem. i guess *smcfancontrol* cannot increase fan speed on my iMac..?

---

### Post by SwedishWings on 2011-08-18
Sorry for the delay. macfanctld is now available for Natty from mactel PPA.

/Mike

---

### Post by ulicigabriel on 2011-10-27
samuaz are you still using the same settings on your mac?
or are you using macfanctld?

Plus do you use 64-bit or 32-bit of ubuntu?

Thanks

---

### Post by jrogers360 on 2011-12-11
+1, thanks for this script!  Works great on my MBP 5,3 running oneiric.

---

### Post by samuaz on 2012-01-13
UPDATED 12/01/2012
- Updated the script, for work in ornerick and kernel 3.x
- apple dkms its no more needed

so its works good in my macbook 4.1 core2duo

temp1_input has change to temp2_input and temp3_input in kernel v3

---

### Post by npydyuan on 2012-02-09
I installed this on my 2011 Mac Mini running Ubuntu 11.10. With tempCalc=highest, the fan speed would change almost constantly, rising, lowering--very annoying although the computer was cool. I have now switched to tempCalc=average, using gedit to edit the configuration as described in the original post, and now so far the fan control seems to work just as smoothly and gradually as it does when I am running Mac OS X.

Thanks! :D

Oh--also I changed the number of sensors to four, since I think that's how many cores this computer's processor has. Would that make sense and be the right setting???

---

### Post by tehwalrus on 2012-02-11
thanks very much, this worked for me in oneric, MBP 5.1. joy! fans that turn! my lap no longer burns, etc.

---

### Post by NeoTm on 2012-02-17
After extensive search I found smcFanControl files on the web site below. The one attached in this thread, can not be downloaded unless you are a member with 50 posts, not easy hahh

[http://wiki.debian.org/DebianOnIntelMacPro?action=AttachFile&do=view&target=photo.png](http://wiki.debian.org/DebianOnIntelMacPro?action=AttachFile&do=view&target=photo.png)

---

### Post by NeoTm on 2012-02-17
Hi all

If you strugling to download smcFanControl files, below is the link on other thread.

[http://wiki.debian.org/DebianOnIntelMacPro?action=AttachFile&do=view&target=smcfancontrol.c](http://wiki.debian.org/DebianOnIntelMacPro?action=AttachFile&do=view&target=smcfancontrol.c)

---

### Post by candlerb on 2012-03-28
Note: in the smcfancontrol script there is a dependency on 'bc' in line 117, which you won't have by default if using ubuntu server. So you may need to do 'apt-get install bc'

Or, since this is a bash script, you could probably just change it to

```
updateSteps=$(( $checkInterval/$updateInterval ))
```

---

### Post by unitedanarchy on 2012-05-08
I did this, But I did it with the first file instead of the 11.10 one and I am on 11.10. I tried installing with the 11.10 one, But I am not sure it is working. I.E My fans are completely off.

---

### Post by SwedishWings on 2012-05-09
> **unitedanarchy said:**
> I did this, But I did it with the first file instead of the 11.10 one and I am on 11.10. I tried installing with the 11.10 one, But I am not sure it is working. I.E My fans are completely off.

Have a look at macfanctld in the Mactel PPA. It's available for Natty, Oneiric and Precise.

/Mike

---

