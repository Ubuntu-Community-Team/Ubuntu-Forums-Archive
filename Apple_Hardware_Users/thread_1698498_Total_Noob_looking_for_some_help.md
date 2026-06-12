---
title: "Total Noob looking for some help"
date: 2011-03-02
forum: Apple Hardware Users
---

### Post by jlalor92 on 2011-03-02
Hey, i just got this itch today to start learning about linux. I have always heard good things about it and wanted to get involved.

Essentially, i have a macbookpro 5,5
What version of linux should i install to get started with this?
I am sure i could figure out the installation myself, but im just looking for some general tips and advice
If anyone could help me out it would be greatly appreciated =]
thanks!

---

### Post by Kirboosy on 2011-03-02
Hi! Welcome to the Forums!


Well I would recommend 10.04 LTS. Its the most recent LTS version so you have two years of official support. Whatever version you do decide to go with the community is always ready to help!

Hope you enjoy using Ubuntu. :D

---

### Post by jlalor92 on 2011-03-02
Ok thank you =] i was reading somewhere that not all of the functionality works on the macbooks with ubuntu, such as the senors, volume control, etc, but all that needs to be done is have them turned on using a command line (which quite frankly i do not really know how to do)
with this 10.04 LTS version, will all the functionality be in place? or will i need to find the command lines to turn on things such as the sensors and airport?

thanks!

---

### Post by Kirboosy on 2011-03-02
I think most of it will work out of the box. I'm not really sure how much command line work you will have to do. 

[This page]("https://help.ubuntu.com/community/SwitchingToUbuntu/FromMacOSX")has lots of useful information

[How to Install Ubuntu on a Macbook]("https://help.ubuntu.com/community/MacBook")

---

### Post by jlalor92 on 2011-03-02
excuse me, i meant macbook pro, is it any different for this compared to the macbook?

---

### Post by dubmartian on 2011-03-02
that link was the starting point for macbook and macbook pro info. kinda hard to navigate.
[https://help.ubuntu.com/community/MacBookPro5-5/Lucid](https://help.ubuntu.com/community/MacBookPro5-5/Lucid)
[https://help.ubuntu.com/community/MacBookPro5-5/Maverick](https://help.ubuntu.com/community/MacBookPro5-5/Maverick)

some of this may be premature...but once you've installed Ubuntu, are connected to the internet, and have your packages configured/updated, you can install lm-sensors & macfanctld for temps & fan info.

heres some examples from my command line:
jmc@natty:~$ sudo apt-get install lm-sensors macfanctld
jmc@natty:~$ sudo sensors -f
coretemp-isa-0000
Adapter: ISA adapter
Core 0:     +109.4°F  (high = +203.0°F, crit = +221.0°F)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:     +109.4°F  (high = +203.0°F, crit = +221.0°F)  

applesmc-isa-0300
Adapter: ISA adapter
Left side  :1999 RPM  (min = 2000 RPM)
Right side :1999 RPM  (min = 2000 RPM)
TB0T:        +87.8°F                                    
TB1T:        +87.8°F                                    
TB2T:        +84.2°F                                    
TC0C:       +109.8°F                                    
TC0D:       +116.6°F                                    
TC0P:       +115.7°F                                    
TC1C:       +125.6°F                                    
TG0D:       +108.5°F                                    
TG0P:       +108.5°F                                    
TG0T:       +113.9°F                                    
TMCD:       +125.6°F                                    
TP0P:       +126.5°F                                    
TPCD:       +141.8°F                                    
Th1H:       +102.6°F                                    
Th2H:       +102.6°F                                    
Tm0P:       +114.3°F                                    
Ts0P:        +82.4°F                                    
Ts0S:        +97.7°F  

jmc@natty:~$ cat /var/log/macfanctl.log
Using parameters:
    temp_avg_floor: 45
    temp_avg_ceiling: 55
    temp_TC0P_floor: 50
    temp_TC0P_ceiling: 58
    temp_TG0P_floor: 50
    temp_TG0P_ceiling: 58
    fan_min: 2000
    log_level: 0
Found 2 fans.
Found 18 sensors:
     1: TB0T - Battery TS_MAX Temp 
     2: TB1T - Battery TS1 Temp 
     3: TB2T - Battery TS2 Temp 
     4: TC0C - ? 
     5: TC0D - CPU 0 Die Temp 
     6: TC0P - CPU 0 Proximity Temp 
     7: TC1C - ? 
     8: TG0D - GPU Die - Digital 
     9: TG0P - GPU 0 Proximity Temp 
    10: TG0T - GPU 0 Die - Analog Temp 
    11: TMCD - ? 
    12: TP0P - ? 
    13: TPCD - ? 
    14: Th1H - ? 
    15: Th2H - Right Fin Stack Proximity Temp 
    16: Tm0P - Battery Charger Proximity Temp 
    17: Ts0P - Palm Rest Temp 
    18: Ts0S - ? 
you may have to reboot for the macfanctl.log to be generated. you can find out what the ?s are somewhere online but i never saved the link. 

am i right that some of the "spaces" in those ubuntu tutorials pertaining to the xorg.conf file may need to be "tabs?" for instance:
Option "RegistryDwords" "EnableBrightnessControl=1"

would need to be:
[tab]Options[tab]"RegistryDwords"[space]"EnableBrightnessControl=1"

or is that a outdated/unnecessary? anyway good luck.

---

