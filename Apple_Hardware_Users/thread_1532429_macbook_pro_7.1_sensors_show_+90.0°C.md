---
title: "macbook pro 7.1 sensors show +90.0°C"
date: 2010-07-16
forum: Apple Hardware Users
---

### Post by keling on 2010-07-16
hello there,

Hope this is the correct place to post my experience, 
I installed on my Macbook pro 7.1 ubuntu Lucid Lynx following the instructions given in [https://help.ubuntu.com/community/MacBookPro7-1/Lucid](https://help.ubuntu.com/community/MacBookPro7-1/Lucid)
I have been able to install and fix most of the issues but I'm worried about what sensors show me:

applesmc-isa-0300
Adapter: ISA adapter
Exhaust  :  1999 RPM  (min = 2000 RPM)
temp1:       +31.5°C                                    
temp2:       +31.5°C                                    
temp3:       +30.2°C                                    
temp4:       +44.8°C                                    
temp5:       +41.8°C                                    
temp6:       +44.0°C                                    
temp7:       +41.0°C                                    
temp8:       +51.0°C                                    
temp9:       +47.0°C                                    
temp10:      +51.0°C                                    
[COLOR=Red]temp11:      +90.0°C [/COLOR]                                   
temp12:      +51.0°C                                    
temp13:      +40.2°C                                    
temp14:      +28.8°C                                    
temp15:      +36.0°C 

does anyone have the same the same values? this 90 is really anoying me and I don't know whether I shall stop the laptop or what to do, I would apreciate some suggestions because looks like I can fry eggs with it

thanks

---

### Post by prophets1976 on 2010-10-08
It´s been a while since you posted this. What have you decided or did you find a solution?
I intalled Ubuntu on my Macbook Pro 7.1 yesterday and I am still not sure if I will keep it...

---

### Post by vegham on 2010-10-10
I'm using a script i wrote since 9.04. It needs root permissions, but keeps my machine cold.

```
#!/bin/bash

# we don`t want to go all the way up to critiacal temp, safe_temp is substracted from critical temp
SAFE_TEMP=10

# AUTOMATIC VALUES BELOW, DON`T EDIT

# CPU critical temp
CPU_CRIT=`cat /sys/devices/platform/coretemp.0/temp1_crit`

# FAN SPEED
FAN1_SPEED_MIN=`cat /sys/devices/platform/applesmc.768/fan1_min`
FAN1_SPEED_MAX=`cat /sys/devices/platform/applesmc.768/fan1_max`
FAN2_SPEED_MIN=`cat /sys/devices/platform/applesmc.768/fan2_min`
FAN2_SPEED_MAX=`cat /sys/devices/platform/applesmc.768/fan2_max`
CPU_CRIT=`expr "(" "$CPU_CRIT" "/" 1000 ")" "-" "$SAFE_TEMP"`

echo 1 > /sys/devices/platform/applesmc.768/fan1_manual
echo 1 > /sys/devices/platform/applesmc.768/fan2_manual

# dynamic values
while [ 1 ]; do

# CPU TEMPS
CPU_TEMP0=`cat /sys/devices/platform/coretemp.0/temp1_input`
CPU_TEMP1=`cat /sys/devices/platform/coretemp.1/temp1_input`
CPU_TEMP=`expr "(" $CPU_TEMP0 + $CPU_TEMP1 ")" "/" 2000`

# calculate
FAN_SPEED=`expr "(" $CPU_TEMP "-" 34 ")" "*" 200`

# if CPU reaches critical - SAFE_TEMP, shut off
if [ "$CPU_TEMP" -gt "$CPU_CRIT" ]; then
shutdown -h now
fi

# don`t go below min limit
if [ "$FAN_SPEED" -le "$FAN1_SPEED_MIN" ]; then
FAN_SPEED=$FAN1_SPEED_MIN;
fi

# don`t go above max limit
if [ "$FAN_SPEED" -gt "$FAN1_SPEED_MAX" ]; then
FAN_SPEED=$FAN1_SPEED_MAX;
fi

# only write if speed has changed
if [ "$FAN_SPEED" != "$FAN_SPEED_OLD" ]; then
echo $CPU_TEMP $FAN_SPEED
echo $FAN_SPEED > /sys/devices/platform/applesmc.768/fan1_output
echo $FAN_SPEED > /sys/devices/platform/applesmc.768/fan2_output
fi

# store old speed
FAN_SPEED_OLD=$FAN_SPEED;

sleep 15
done
```

---

### Post by alexmurray on 2010-10-10
You should never set fanX_manual to 1 since this overrides the automatic fan control of the SMC controller - also don't set fanX_output - instead leave fanX_manual as 0 and set fanX_min instead - this ensures the minimum speed of the fan is the value you set, but allows the firmware to increase the fan speed if it deems it necessary - this should help avoiding frying your machine if your script fails or goes haywire etc - or if your script gets killed etc.

For the sake of your machine, **DON'T SET fanX_manual to 1 and instead set fanX_min instead of fanX_output**

---

