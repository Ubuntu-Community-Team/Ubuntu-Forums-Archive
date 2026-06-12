---
title: "imac fan out of control 2"
date: 2017-02-01
forum: Apple Hardware Users
---

### Post by cantonbean on 2017-02-01
Hello all,

I found this brilliant script on here (on an older thread) to solve the issue in the absence of the SSD fan control application for Linux :-

smartfancontrol.sh

#### enter your preferred values here ##################
speed_min=1100 #RPM
speed_max=1200 #RPM
temp_min=46  #degrees celsius 
temp_max=60 #degrees celsius 

##########  Do not edit below this line ###################

echo 1 > /sys/devices/platform/applesmc.768/fan2_manual

while [ 1 ]
do

    temp=$(/usr/sbin/smartctl -A /dev/sda | grep ^194 | awk '{print $10}')
 
    if [[ $temp -lt $temp_min ]]; then
        speed=$speed_min
    elif [[ $temp -gt $temp_max ]]; then
        speed=$speed_max
    else
        x=$(($speed_max-$speed_min))
        y=$(($(($temp-$temp_min))*100))
        z=$(($(($temp_max-$temp_min))*100))
        a=$(($x*$y/$z))
        speed=$(($a+$speed_min))
    fi

    echo $speed >/sys/devices/platform/applesmc.768/fan2_output

    printf '[ %i  C | %i  rpm ]\n' $temp  $speed

    sleep 60
    done

I would like to run this script at start up automatically and it needs root privileges to run. I've looked at a few ways to do this but all are rather confusing. Would someone be kind enough to tell me how to get this to run automatically at start up please?

---

### Post by MikeBraxner on 2017-02-05
Save your script locally, e.g. as ~/bin/ssd_fan.sh, and start it from within /etc/rc.local ... that should do the trick.

---

