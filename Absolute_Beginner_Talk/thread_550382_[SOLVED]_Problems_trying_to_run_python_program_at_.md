---
title: "[SOLVED] Problems trying to run python program at startup"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by mattorama on 2007-09-13
Hello,

I want to start pyTivo when my computer boots. 

I have the following file named pyTivoStartup:

```

# chkconfig: 2345 99 05
# description: pyTivo server

### INIT INFO
# Provides: pytivo
# Required-Start: $network
# Required-Stop: $network
# Default-Start: 2 3 4 5
# Default-Stop: 0 1 6
# Short-description: pyTivo server
# Description: Start and stop the pyTivo server.
### END INIT INFO

RETVAL=0

cd /etc/pyTivo

start() {
echo -n "Starting pyTivo: "
pgrep -f pyTivo.py
RETVAL=$?
[ $RETVAL -eq 0 ] && echo "pyTivo already running: Exiting" && exit 1

python2.5 /etc/pyTivo/pyTivo.py > /dev/null 2>&1 &
#python2.5 /etc/pyTivo/pyTivo.py
RETVAL=$?
[ $RETVAL -eq 0 ] && echo -n "done"
echo
return $RETVAL
}

stop() {
echo -n "Stopping pyTivo: "
pkill -f pyTivo.py
RETVAL=$?
echo
[ $RETVAL -eq 0 ] && echo -n "done"
echo
return $RETVAL
}

# See how we were called.
case "$1" in
start)
start
;;
stop)
stop
;;
restart|reload)
stop
sleep 1
start
RETVAL=$?
;;
*)
echo "Usage: $0 {start|stop|restart}"
exit 1
esac
exit $RETVAL

```

I copied this into /etc/inet.d and made it executable.

I then used sysv-rc-conf and set it up at runlevels 2,3,4,5

If I reboot and then login and run "ps -ax" I don't see it running.

**If I run it manually it works** and I can see it in "ps -ax".

Any help is greatly appreciated!

-Matt

---

### Post by mattorama on 2007-09-14
I might be able to diagnose this problem myself if there were a way to view the log output from the startup. Does inet.d have a log that I can view?

-Matt

---

### Post by mattorama on 2007-09-16
I couldn't get my original script to work so I edited bootmisc.sh and called my python script from there. 

This worked! 

Not sure why the other didn't.

I'm satisfied enough with this solution to move on to other things.

-Matt

---

