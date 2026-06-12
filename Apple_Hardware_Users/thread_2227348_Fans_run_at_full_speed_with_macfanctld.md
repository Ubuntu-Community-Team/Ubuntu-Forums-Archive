---
title: "Fans run at full speed with macfanctld"
date: 2014-06-01
forum: Apple Hardware Users
---

### Post by joeDirt420 on 2014-06-01
I never had an issue with macfanctld before but after installing ubuntu 14.04 and then macfanctld and applscm-dkms the HDD fan and ODD fans are running at full speed. I have looked every where but can't figure out how to fix the full speed fan issue. Any help would be greatly appreciated..

Output for "sensors"

```

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +58.0°C  (high = +80.0°C, crit = +86.0°C)
Core 0:         +58.0°C  (high = +80.0°C, crit = +86.0°C)
Core 1:         +56.0°C  (high = +80.0°C, crit = +86.0°C)
Core 2:         +58.0°C  (high = +80.0°C, crit = +86.0°C)
Core 3:         +58.0°C  (high = +80.0°C, crit = +86.0°C)


applesmc-isa-0300
Adapter: ISA adapter
ODD :        5544 RPM  (min = 6200 RPM, max = 4350 RPM)
HDD :        6200 RPM  (min = 6200 RPM, max = 6300 RPM)
CPU :        1199 RPM  (min = 1200 RPM, max = 4000 RPM)
TA0P:         +35.5°C  
TA0V:         +35.5°C  
TA0p:         +36.0°C  
TC0H:         +54.5°C  
TC0P:         +51.0°C  
TC0c:         +57.0°C  
TC0h:         +54.5°C  
TC0p:         +51.0°C  
TC1c:         +57.0°C  
TC2c:         +57.0°C  
TC3c:         +57.0°C  
TCGc:         +58.0°C  
TCSc:         +54.0°C  
TCXc:         +57.2°C  
TG0D:         +56.2°C  
TG0H:         +50.8°C  
TG0d:         +56.2°C  
TG0h:         +50.8°C  
TG0p:         +51.0°C  
TH0O:          -7.0°C  
TH1O:          -7.0°C  
TL0P:         +40.2°C  
TL0V:         +42.2°C  
TL0p:         +51.8°C  

```


Output of "watch sensors"

```

Every 2.0s: sensors                                              Sun Jun  1 08:54:28 2014


coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +59.0°C  (high = +80.0°C, crit = +86.0°C)
Core 0:         +58.0°C  (high = +80.0°C, crit = +86.0°C)
Core 1:         +55.0°C  (high = +80.0°C, crit = +86.0°C)
Core 2:         +57.0°C  (high = +80.0°C, crit = +86.0°C)
Core 3:         +59.0°C  (high = +80.0°C, crit = +86.0°C)


applesmc-isa-0300
Adapter: ISA adapter
ODD :        5544 RPM  (min = 6200 RPM, max = 4350 RPM)
HDD :        6196 RPM  (min = 6200 RPM, max = 6300 RPM)
CPU :        1200 RPM  (min = 1200 RPM, max = 4000 RPM)
TA0P:         +35.8°C
TA0V:         +35.5°C
TA0p:         +36.2°C
TC0H:         +54.5°C
TC0P:         +51.0°C
TC0c:         +57.0°C
TC0h:         +54.5°C
TC0p:         +51.0°C
TC1c:         +57.0°C

```

Here is my macfanctld.conf

```

# Config file for macfanctl daemon
#
# Note: 0 < temp_X_floor < temp_X_ceiling
#       0 < fan_min < 6200       


fan_min: 2000


temp_max_floor: 65
temp_max_ceiling: 70
temp_max_fan_min: 4000


temp_avg_floor: 45
temp_avg_ceiling: 55


temp_TC0P_floor: 50
temp_TC0P_ceiling: 58


temp_TG0P_floor: 50
temp_TG0P_ceiling: 58


# Add sensors to be excluded here, separated by space, i.e.
# exclude: 1 7
# will disable reading of sensors temp1_input and temp7_input.


exclude:


# log_level values:
#   0: Startup / Exit logging only
#   1: Basic temp / fan logging
#   2: Log all sensors  


log_level: 0

```

---

### Post by este.el.paz on 2014-06-02
@JoeD:

I personally don't know enough to be able to give detailed instructions, but if you look down in the list a few threads to my "Is ppa for macfanctld updated for 14.04"????  can't remember . . . but Mike B gives me some pretty detailed instructions there on getting macfanctld set up and you might figure it out . . . ???

But, on quick viewing of your temps, there are two numbers showing "-7" . . . from what I've learned, macfanctld does an averaging of the temps to decide when to turn the fan(s) on, so I believe those are the two that you have to "exclude" in your config  file . . . you'd have to read through my thread or other threads from Mike or Swedish Wings to know how to decide how to identify which are those to be excluded.

e.e.p.

---

### Post by MikeBraxner on 2014-06-03
The answer is in your somewhat anomalous sensor readings...
> **joeDirt420 said:**
> 
ODD :        **5544** **RPM**  **(min = 6200 RPM, max = 4350 RPM)**
HDD :        6200 RPM  **(min = 6200 RPM, max = 6300 RPM)**
CPU :        1199 RPM  (min = 1200 RPM, max = 4000 RPM)


While the CPU fan speed specs seem fine, the ***minimum*** fan speed for both ODD and HDD is given as ***6200***, while the ***maximum*** speed reads ***4350*** for ODD and ***6300*** for HDD. In other words, while the HDD fan speed is allowed to fluctuate between 6200 and 6300 rpm, the fan speed for ODD can NEVER drop below its minimum of 6200 rpm ... which is where things go wonky, since *sensors* reports the ***actual*** fan speed as 5544 rpm, i.e. ***below*** the alleged minimum ... hence, anomalous.

For starters, I ***don't*** ***know*** whether macfanctld **would** adjust the fans for ODD and/or HDD, though I *assume* it *should* be able to adjust the fan speeds correctly, if, *and only if*, the appropriate minimum and maximum values are set correctly. However, I don't think you'll be able to do this via macfanctld.conf, since it (as far as I'm aware) only uses the *fan_min* key to identify a *general* minimum fan speed setting, which cannot undercut an existing, ***explicitly set*** minimum setting in */sys/devices/platform/applesmc.768/.* You could have a look at the available fan related stuff there, i.e. *ls fan** should give you something like ...
```
fan1_input  fan1_manual  fan1_min     fan1_safe   fan2_label   fan2_max  fan2_output
fan1_label  fan1_max     fan1_output  fan2_input  fan2_manual  fan2_min  fan2_safe
```

Just identify which one references ODD, i.e. check the labeling (e.g. *cat fan1_label*, *cat fan2_label, *etc) until you find the right one. For the purposes at hand I will ***ASSUME*** this to be the first, i.e. *fan1*. Double check the pre-set minimum and maximum fan speeds, e.g. *cat fan1_min* and *cat fan1_max,* which should match the ones reported by *sensors*, i.e. minimum 6200 and maximum 4350 respectively. If this is the case, then you know ***where one*** problem lies, i.e. switched min/max values, which you could correct via an ***rc.d*** script along the lines of ...
```
echo 4350 > [I]/sys/devices/platform/applesmc.768/fan1_min
[/I]echo 6200 > */sys/devices/platform/applesmc.768/fan1_max*
```

For your HDD fan, the value range reported by sensors is *viable*, but does seem a little high. Again, you could alter these settings via an rc.d script adjustment, but you'd realllyyyy want to be sure you got the *correct* values ... which I certainly cannot comment on, seeing that you didn't even specify what mac your using.

Next, your *actual* CPU fan speed, as well as the *minimum*, as reported by sensors is below the minimum fan speed *specified* in your macfanctld.conf ... are you certain you are ***actually running*** macfanctld??? Mind you, I assume you correctly installed lmsensors, ***including*** the adjustment run needed, and followed the installation instructions for macfanctld (see man page).

Finally, as este.el.paz already mentioned, two of your sensors report bogus temps (TH0O:          -7.0°C, TH1O:          -7.0°C) which would certainly screw with macfanctld's temperature averaging (see man macfanctld) ... you need to add those to you macfanctld.conf's exclude line.

---

### Post by joeDirt420 on 2014-06-06
> **MikeBraxner said:**
> The answer is in your somewhat anomalous sensor readings...


While the CPU fan speed specs seem fine, the ***minimum*** fan speed for both ODD and HDD is given as ***6200***, while the ***maximum*** speed reads ***4350*** for ODD and ***6300*** for HDD. In other words, while the HDD fan speed is allowed to fluctuate between 6200 and 6300 rpm, the fan speed for ODD can NEVER drop below its minimum of 6200 rpm ... which is where things go wonky, since *sensors* reports the ***actual*** fan speed as 5544 rpm, i.e. ***below*** the alleged minimum ... hence, anomalous.

For starters, I ***don't*** ***know*** whether macfanctld **would** adjust the fans for ODD and/or HDD, though I *assume* it *should* be able to adjust the fan speeds correctly, if, *and only if*, the appropriate minimum and maximum values are set correctly. However, I don't think you'll be able to do this via macfanctld.conf, since it (as far as I'm aware) only uses the *fan_min* key to identify a *general* minimum fan speed setting, which cannot undercut an existing, ***explicitly set*** minimum setting in */sys/devices/platform/applesmc.768/.* You could have a look at the available fan related stuff there, i.e. *ls fan** should give you something like ...
```
fan1_input  fan1_manual  fan1_min     fan1_safe   fan2_label   fan2_max  fan2_output
fan1_label  fan1_max     fan1_output  fan2_input  fan2_manual  fan2_min  fan2_safe
```

Just identify which one references ODD, i.e. check the labeling (e.g. *cat fan1_label*, *cat fan2_label, *etc) until you find the right one. For the purposes at hand I will ***ASSUME*** this to be the first, i.e. *fan1*. Double check the pre-set minimum and maximum fan speeds, e.g. *cat fan1_min* and *cat fan1_max,* which should match the ones reported by *sensors*, i.e. minimum 6200 and maximum 4350 respectively. If this is the case, then you know ***where one*** problem lies, i.e. switched min/max values, which you could correct via an ***rc.d*** script along the lines of ...
```
echo 4350 > [I]/sys/devices/platform/applesmc.768/fan1_min
[/I]echo 6200 > */sys/devices/platform/applesmc.768/fan1_max*
```

For your HDD fan, the value range reported by sensors is *viable*, but does seem a little high. Again, you could alter these settings via an rc.d script adjustment, but you'd realllyyyy want to be sure you got the *correct* values ... which I certainly cannot comment on, seeing that you didn't even specify what mac your using.

Next, your *actual* CPU fan speed, as well as the *minimum*, as reported by sensors is below the minimum fan speed *specified* in your macfanctld.conf ... are you certain you are ***actually running*** macfanctld??? Mind you, I assume you correctly installed lmsensors, ***including*** the adjustment run needed, and followed the installation instructions for macfanctld (see man page).

Finally, as este.el.paz already mentioned, two of your sensors report bogus temps (TH0O:          -7.0°C, TH1O:          -7.0°C) which would certainly screw with macfanctld's temperature averaging (see man macfanctld) ... you need to add those to you macfanctld.conf's exclude line.

Thank you for the reply Mike. I installed macfanctld from the software center and applesmc-dkms from the mactel repo. I did install lmsensors. Also I am unable to change the min fan speeds at */sys/devices/platform/applesmc.768/fan1_min. *I get permission error even when using sudo. Is there a certain way that macfanctld should be installed because like I said I never had an issue with it before.

By the way I have a 2011 21.5 inch iMac. When I wake my computer up from suspend the min fan speed is 2000 like it should be but then it gradually increases to max speed even if I am not doing anything..

---

### Post by MikeBraxner on 2014-06-07
***lmsensors*** ... Check [https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto) for the proper install procedure (*sudo sensors-detect*) ... it's kind of important ;-)

***"...unable to change the min fan speeds ... permission error" ...*** That's why I suggested an ***rc.d*** script. Simplified, presuming the previously indicated convention, add the following to ***/etc/rc.local*** ...
```
# ensuring proper fan speed settings for ODD fan ...
if [ -f /sys/devices/platform/applesmc.768/fan1_min ]; then
    echo "/etc/rc.local $(echo "[`date`]")   -->   Adjusting fan speed settings for ODD fan "  >> /var/log/rc.local.log
    echo 4350 > /sys/devices/platform/applesmc.768/fan1_min
    echo 6200 > /sys/devices/platform/applesmc.768/fan1_max
fi
```

***macfanctld*** ... You need to adjust the appropriate temp ranges and which sensors to exclude, so that macfanctld utilises the appropriate temperature averages (**READ** *man macfanctld*) ... you could also take a look at [http://ubuntuforums.org/showthread.php?t=2212785&p=12970649#post12970649](http://ubuntuforums.org/showthread.php?t=2212785&p=12970649#post12970649)

---

### Post by AllBuntu on 2014-10-09
There is some problem with the fan control background adjustments. I use a MacMini1,1 which is i386-efi and 14.04 LTS.
check out:
ls /sys/devices/platform/applesmc.768

You can notice your fan momentarily slow down if you try:
echo 100 | sudo tee /sys/devices/platform/applesmc.768/fan1_output

manual mode works:
sudo service macfanctld stop
echo 1 | sudo tee /sys/devices/platform/applesmc.768/fan1_manual
1
echo 1500 | sudo tee /sys/devices/platform/applesmc.768/fan1_output
1000

Check your sensors for a good rpm value ie. between like 100 and 5,000. My value was 1,500.
Typically run all less than 60 C
date; sensors

sound of silence...

---

### Post by rurodrig on 2014-10-18
> **MikeBraxner said:**
> ***lmsensors*** ... Check [https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto) for the proper install procedure (*sudo sensors-detect*) ... it's kind of important ;-)

***"...unable to change the min fan speeds ... permission error" ...*** That's why I suggested an ***rc.d*** script. Simplified, presuming the previously indicated convention, add the following to ***/etc/rc.local*** ...
```
# ensuring proper fan speed settings for ODD fan ...
if [ -f /sys/devices/platform/applesmc.768/fan1_min ]; then
    echo "/etc/rc.local $(echo "[`date`]")   -->   Adjusting fan speed settings for ODD fan "  >> /var/log/rc.local.log
    echo 4350 > /sys/devices/platform/applesmc.768/fan1_min
    echo 6200 > /sys/devices/platform/applesmc.768/fan1_max
fi
```

***macfanctld*** ... You need to adjust the appropriate temp ranges and which sensors to exclude, so that macfanctld utilises the appropriate temperature averages (**READ** *man macfanctld*) ... you could also take a look at [http://ubuntuforums.org/showthread.php?t=2212785&p=12970649#post12970649](http://ubuntuforums.org/showthread.php?t=2212785&p=12970649#post12970649)


I have the same fan issues and added that to rc.local (both before and after the exit 0 line since I wasn't sure what I was doing) and my fans still run full bore all the time.

I'm on a Macbook 7.1 (13 inch) so I only have one fan as far as I know.

Here's the sensors printout:

Adapter: ISA adapter
Core 0:       +40.0°C  (high = +105.0°C, crit = +105.0°C)
Core 1:       +42.0°C  (high = +105.0°C, crit = +105.0°C)

applesmc-isa-0300
Adapter: ISA adapter
Exhaust  :   6196 RPM  (min = 6200 RPM, max = 6200 RPM)
TB0T:         +28.8°C  
TB1T:         +28.8°C  
TB2T:         +28.5°C  
TC0D:         +45.2°C  
TC0P:         +39.5°C  
TN0D:         +42.5°C  
TN0P:         +35.5°C  
TN0S:         +50.2°C  
TN1D:         +49.0°C  
TN1F:         +50.2°C  
TN1G:         +90.0°C  
TN1S:         +50.2°C  
Th1H:         +37.0°C  
Ts0P:         +28.8°C  
Ts0S:         +33.5°C  


I did change the echo 4350 to echo 2000 because I wanted the min rpm at 2000 (to match macfan and apple).

Any other ideas anyone?

---

### Post by MikeBraxner on 2014-10-19
A thought as to setting fanX_min: should work simple enough from either an rc.d script, or a root shell. However, since the initial value ought to be supplied by apple.smc kernel module, there might be a possibility of a 'corrupted' version on your system ... kernel update/change/amend apple.smc module???

In the meantime, you might want to check on some old threads, say, [http://ubuntuforums.org/archive/index.php/t-1754431.html](http://ubuntuforums.org/archive/index.php/t-1754431.html), [https://bbs.archlinux.org/viewtopic.php?pid=551105](https://bbs.archlinux.org/viewtopic.php?pid=551105), [http://ineed.coffee/923/an-enhanced-version-of-simple-macbook-pro-fan-daemon-for-linux/](http://ineed.coffee/923/an-enhanced-version-of-simple-macbook-pro-fan-daemon-for-linux/), or [http://rbfzone.blogspot.com/2012/04/manual-fan-speed-ubuntu-1204-macbook.html](http://rbfzone.blogspot.com/2012/04/manual-fan-speed-ubuntu-1204-macbook.html)  No guarantees, but you could give it a try ;-)

---

### Post by rurodrig on 2014-10-19
Thanks for pointing me in the right direction.

I finally got it to work by excluding whatever TN1G sensor is in macfanctl.conf.  It was always at 90.   In mine (Macbook Pro 7.1, 13" mid 2010) it was sensor 11. The assumption that the first one on the sensor list is sensor 1, etc worked.

I also simplified the rc.local script to be : 

echo 2000 > /sys/devices/platform/applesmc.768/fan1_min 

...and apparently it did have to be before exit 0.

That script wasn't working until I excluded the TN1G.

Now my Macbook is nice and quiet.  The Fan runs at around 2000 unless I'm doing lots of stuff.  TN1G is still at 90, but everything else is reasonable.

Sensor output now is:
Adapter: ISA adapter
Core 0:       +46.0°C  (high = +105.0°C, crit = +105.0°C)
Core 1:       +48.0°C  (high = +105.0°C, crit = +105.0°C)

applesmc-isa-0300
Adapter: ISA adapter
Exhaust  :   1995 RPM  (min = 2000 RPM, max = 6200 RPM)
TB0T:         +29.2°C  
TB1T:         +29.2°C  
TB2T:         +28.2°C  
TC0D:         +53.5°C  
TC0P:         +46.5°C  
TN0D:         +49.8°C  
TN0P:         +42.2°C  
TN0S:         +56.8°C  
TN1D:         +56.0°C  
TN1F:         +56.8°C  
TN1G:         +90.0°C  
TN1S:         +56.8°C  
Th1H:         +44.5°C  
Ts0P:         +28.0°C  
Ts0S:         +37.8°C

---

### Post by duderdice on 2015-04-04
I have a MacBookPro4,1 (early 2008 MacBook Pro 17")  and it has always had problems with getting too hot under linux.  The "macfanctld" utility works great.  

Like rurodrig mentions, I had to exclude two fans who seemingly were reporting incorrectly (#8 & #9)   They caused the fan to always run high because they exceeded the Max Temp and triggered the fan speed increase to max.  By excluding these two temp inputs, the system runs normally and adapts to intensive work (hence heat) by spinning up the fans, as needed.  Its enabled me to tackle one of the biggest hassles using Linux on this computer.  Thanks ~detly for still maintaining these utilities for those of us who need them.  Its very misleading to see the Ubuntu MacTel wiki page to indicate that all utilities are merged into the main trunk and that MacTell PPAs are no longer needed.  This is still very much a necessary tool on my laptop, otherwise it runs REALLY HOT.  Thanks for saving my lap!

FYI, here are my sensors readings...

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +44.0°C  (high = +105.0°C, crit = +105.0°C)
Core 1:       +43.0°C  (high = +105.0°C, crit = +105.0°C)


applesmc-isa-0300
Adapter: ISA adapter
Left side  : 3781 RPM  (min = 3780 RPM, max = 6000 RPM)
fan2:        3777 RPM  (min = 3780 RPM, max = 6000 RPM)
TALP:         +38.0°C  
TB0T:         +33.5°C  
TC0D:         +53.8°C  
TC0P:         +49.8°C  
TG0D:         +64.5°C  
TG0H:         +52.0°C  
TG0V:         +52.8°C  
TGTV:        +127.0°C   <-- temp sensor #8
TTF0:         +70.0°C      <-- temp sensor #9
TW0P:         +51.5°C  
Th0H:         +54.2°C  
Th1H:         +43.8°C  
Th2H:         +43.2°C  
Tm0P:         +46.0°C  
Ts0P:         +37.5°C  


nouveau-pci-0100
Adapter: PCI adapter
temp1:        +64.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +110.0°C, hyst =  +3.0°C)
                       (emerg = +110.0°C, hyst = +10.0°C)

---

