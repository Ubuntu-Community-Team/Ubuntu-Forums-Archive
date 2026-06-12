---
title: "Minimum Fan Speed MacBook"
date: 2009-11-28
forum: Apple Hardware Users
---

### Post by CosyCat on 2009-11-28
I´ trying this out in Karmic(2.6.31-15)
[https://help.ubuntu.com/community/MacBook2-1/Jaunty#Minimum%20Fan%20Speed](https://help.ubuntu.com/community/MacBook2-1/Jaunty#Minimum%20Fan%20Speed)

but I can´t get it to work.

I can only set it manually writing this in terminal 
echo 3200 | sudo tee -a /sys/devices/platform/applesmc.768/fan1_min
but it´s back to 1800 after restart.

when I edit **/etc/init.d/acpid **exactly where in should I place
echo 3200 > /sys/devices/platform/applesmc.768/fan1_min

or is it this line(tried both) echo 3200 | sudo tee -a /sys/devices/platform/applesmc.768/fan1_min because this is the only line working setting it manually in terminal.


this is my acpid right now having the line just before exit


#!/bin/sh -e
# upstart-job
#
# Symlink target for initscripts that have been converted to Upstart.

set -e

INITSCRIPT="$(basename "$0")"
JOB="${INITSCRIPT%.sh}"

if [ "$JOB" = "upstart-job" ]; then
    if [ -z "$1" ]; then
        echo "Usage: upstart-job JOB COMMAND" 1>&2
    exit 1
    fi

    JOB="$1"
    INITSCRIPT="$1"
    shift
else
    if [ -z "$1" ]; then
        echo "Usage: $0 COMMAND" 1>&2
    exit 1
    fi
fi

COMMAND="$1"
shift


if [ -z "$DPKG_MAINTSCRIPT_PACKAGE" ]; then
    ECHO=echo
else
    ECHO=:
fi

$ECHO "Rather than invoking init scripts through /etc/init.d, use the service(8)"
$ECHO "utility, e.g. service $INITSCRIPT $COMMAND"

case $COMMAND in
status)
    $ECHO
    $ECHO "Since the script you are attempting to invoke has been converted to an"
    $ECHO "Upstart job, you may also use the $COMMAND(8) utility, e.g. $COMMAND $JOB"
    $COMMAND "$JOB"
    ;;
start|stop|restart)
    $ECHO
    $ECHO "Since the script you are attempting to invoke has been converted to an"
    $ECHO "Upstart job, you may also use the $COMMAND(8) utility, e.g. $COMMAND $JOB"
    PID=$(status "$JOB" 2>/dev/null | awk '/[0-9]$/ { print $NF }')
    if [ -z "$PID" ] && [ "$COMMAND" = "stop" ]; then
        exit 0
    elif [ -n "$PID" ] && [ "$COMMAND" = "start" ]; then
        exit 0
    elif [ -z "$PID" ] && [ "$COMMAND" = "restart" ]; then
        start "$JOB"
        exit 0
    fi
    $COMMAND "$JOB"
    ;;
reload|force-reload)
    $ECHO
    $ECHO "Since the script you are attempting to invoke has been converted to an"
    $ECHO "Upstart job, you may also use the $COMMAND(8) utility, e.g. $COMMAND $JOB"
    reload "$JOB"
    ;;
*)
    $ECHO
    $ECHO "The script you are attempting to invoke has been converted to an Upstart" 1>&2
    $ECHO "job, but $COMMAND is not supported for Upstart jobs." 1>&2
echo 3200 > /sys/devices/platform/applesmc.768/fan1_min
exit 1
esac









thx

---

### Post by dennis123123 on 2009-11-28
just put it in /etc/rc.local

---

### Post by CosyCat on 2009-12-02
worked thx

---

### Post by luigi.viggiano on 2009-12-02
I use mfc-daemon ([http://github.com/xiangfu/mfc-daemon](http://github.com/xiangfu/mfc-daemon)), I made my own patch ([http://ubuntuforums.org/showthread.php?t=1341198](http://ubuntuforums.org/showthread.php?t=1341198)) for a misbehavior, and it works great on my system now.

I start it in rc.local as well, and I have CPU and GPU stable around 60°C.

---

### Post by CosyCat on 2009-12-02
thx will try that

edit: whats temp1 - temp10 stand for on sensors

Exhaust  :  3473 RPM  (min = 3200 RPM)
temp1:       +33.8°C                                    
temp2:       +63.8°C                                    
temp3:       +58.0°C                                    
temp4:       +50.2°C                                    
temp5:       +53.8°C                                    
temp6:       +56.2°C                                    
temp7:       +59.0°C                                    
temp8:       +58.2°C                                    
temp9:       +58.8°C                                    
temp10:      +59.5°C

---

