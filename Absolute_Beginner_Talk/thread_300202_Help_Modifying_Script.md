---
title: "Help Modifying Script"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by davebed on 2006-11-15
I am hoping someone can help me modify my **power.sh** script. From what I understand, this script is called when I switch to battery *and* when I plug the AC back in. (This way, when I run Beryl, I'll still have my display turn off automatically)

I would like to add the following command when it's running on battery (ie. when Laptop-mode engages:
```
DISPLAY=:0 xset dpms 60
```

And then add the following for when it's back on AC (ie. when laptop-mode disengages):
```
DISPLAY=:0 xset dpms 180
```  

Here is my Power.sh script. Could someone show me **where** and **how** to add this command?  Thanks

```
#!/bin/bash

. /etc/default/acpi-support
. /usr/share/acpi-support/power-funcs

function laptop_mode_enable {
    $LAPTOP_MODE start
    
    for x in /sys/bus/ide/devices/*/block; do 
	drive=$(basename $(readlink $x));
	$HDPARM -S 100 /dev/$drive 2>/dev/null
	$HDPARM -B 128 /dev/$drive 2>/dev/null
    done
    
    for x in /sys/bus/scsi/devices/*/block; do 
	drive=$(basename $(readlink $x));
	$HDPARM -S 100 /dev/$drive 2>/dev/null
	$HDPARM -B 128 /dev/$drive 2>/dev/null
    done
}

function laptop_mode_disable {
    for x in /sys/bus/ide/devices/*/block; do 
	drive=$(basename $(readlink $x));
	$HDPARM -S 800 /dev/$drive 2>/dev/null
	$HDPARM -B 255 /dev/$drive 2>/dev/null
    done
    for x in /sys/bus/scsi/devices/*/block; do 
	drive=$(basename $(readlink $x));
	$HDPARM -S 800 /dev/$drive 2>/dev/null
	$HDPARM -B 255 /dev/$drive 2>/dev/null
    done
    $LAPTOP_MODE stop
}

getState;

checkStateChanged;

shopt -s nullglob

for x in /proc/acpi/ac_adapter/*; do
    grep -q off-line $x/state

    if [ $? = 0 ] && [ x$1 != xstop ]; then	
	for SCRIPT in /etc/acpi/battery.d/*.sh; do
	    . $SCRIPT
	done
	if [ x$ENABLE_LAPTOP_MODE = xtrue ]; then
	    (sleep 5 && laptop_mode_enable)&
	fi
    else
	for SCRIPT in /etc/acpi/ac.d/*.sh; do
	    . $SCRIPT
	done
	if [ x$ENABLE_LAPTOP_MODE = xtrue ]; then
	    (sleep 5 && laptop_mode_disable)&
	fi
    fi
done

```

---

### Post by davebed on 2006-11-16
Anyone? 
Thanks.

---

