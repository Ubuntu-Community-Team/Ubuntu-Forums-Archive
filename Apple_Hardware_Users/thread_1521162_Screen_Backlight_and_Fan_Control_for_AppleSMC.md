---
title: "Screen Backlight and Fan Control for AppleSMC"
date: 2010-06-30
forum: Apple Hardware Users
---

### Post by Maletor on 2010-06-30
How can I adjust screen backlight from commandline?
I'm trying to write a script to audjust it based on what it gathers from AppleSMC.

Also, I updated a fan control script based on this:
[https://wiki.ubuntu.com/MacBookPro/SantaRosaFanControl](https://wiki.ubuntu.com/MacBookPro/SantaRosaFanControl)

```
# version 0.5 - 20080120
# A temperature daemon to help for a cooler MacBookPro 3.1
# Now also changes the power saving mode for the HD depending on 
# on/off-line mode.
# Author nick barcet nickNOSPAM AT barcet DOT com

### W A R N I N G ###

# No guaranty whatsoever that it will do good to your computer.
# You can blame yourself for installing this if your processor
# decides to die tomorrow

do_init()
{
# I'm pretty happy with the following  values but feel free to
# play with them.  Just keep an eye on the values return by the sensors
# package.
# We set different value for on and off line, as we don't care
# about saving power when on-line.
	if (cat /proc/acpi/ac_adapter/ADP1/state | grep on-line > /dev/null); then
# We are online, be pretty cool
		[ $debug -eq 1 ] && echo "state:                   on-line"
			MIN=475 # temp in degree celsius x 10
			MAX=540
			let "RATIO = 6000 / ($MAX - $MIN)"
#no need for much hd power saving when on-line
			sudo hdparm -B 200 /dev/sda 
	else
		[ $debug -eq 1 ] && echo "state:                   off-line"
			MIN=510 # temp in degree celsius x 10
			MAX=590
			let "RATIO = 6000 / ($MAX - $MIN)"
#be more agressive on hd power-savings when off-line
			sudo hdparm -B 50 /dev/sda
			fi
			let "TARGET = ( ($MAX - $MIN)/3 ) + $MIN"
#       let "HIGH = ( ($MAX - $MIN)/3 ) + $TARGET"
}

get_temp()
{
	TEMP1=`cat /sys/devices/platform/applesmc.768/temp5_input`
        TEMP2=`cat /sys/devices/platform/applesmc.768/temp8_input`
        TEMP3=`cat /sys/devices/platform/applesmc.768/temp3_input`
	TEMP4=`cat /sys/devices/platform/applesmc.768/temp4_input`
        TEMP5=`nvidia-settings -q GPUCoreTemp | grep 'Attribute' | awk '{print  $4 * 1000}'`
    	let "TEMP = ($TEMP1 + $TEMP2 + $TEMP3 + $TEMP4 + $TEMP5)/ 500"
}

debug=1
do_init
count=1
maxtempcount=0

while [ true ]; do 

get_temp

[ $debug -eq 1 ] && echo "average temp: $TEMP (target: $TARGET, max: $MAX)" 

let "SPEED = ($TEMP - $MIN) * $RATIO"    

[ $debug -eq 1 ] && echo "Speed: $SPEED"

# Just to make sur we do not set fan >6000 or <0
if [ $SPEED -gt 6000 ]; then
SPEED=6000
elif [ $SPEED -lt 1 ]; then
SPEED=1
	elif [ $TEMP -lt $TARGET ]; then
#let autoregulation work (if it does)
	SPEED=1  
	fi

	[ $debug -eq 1 ] && echo "set fan speed to: $SPEED (step: $RATIO)"
	echo $SPEED | sudo tee /sys/devices/platform/applesmc.768/fan1_min

	if [ $TEMP -gt $MAX ]; then
	[ $debug -eq 1 ] && echo "temp: $TEMP > max: $MAX"
	let "maxtempcount = $maxtempcount + 1"
	if [ $maxtempcount -gt 3 ]; then
	while [ $TEMP -gt $TARGET ]; do
	[ $debug -eq 1 ] && echo "Force fan speed to: 6000 until temp ($TEMP) = $TARGET"
	echo 6000 | sudo tee /sys/devices/platform/applesmc.768/fan1_min
	sleep 10
	get_temp
	let "count = $count + 2"
	done
	maxtempcount=0
	else
	sleep 5
	let "count = $count+1"
	fi
	elif [ $SPEED -lt 2 ]; then
# Sleep longer when autoregulating
	sleep 20
	let "count = $count+4"
	else
	sleep 5
	let "count = $count+1"
	fi

	if [ $count -gt 10 ]; then
	count=0
	do_init
	fi
	done

```

---

