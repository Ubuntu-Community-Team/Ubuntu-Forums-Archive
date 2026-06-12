---
title: "My Irtrans daemon won't work"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by skroops on 2007-12-30
I downloaded a daemon for irserver to run at bootup /etc/init.d/startir:

```
#!/bin/sh -e
#
# /etc/init.d/startir 

NAME="Irserver"
FNAME="irserver64"
PIDNAME="/var/run/irserver.pid"

irserver_start() {
        ( cd /usr/local/irtrans && ./irserver64 -pidfile ${PIDNAME} 
-daemon /dev/ttyUSB0 ) &        
        echo "$NAME tried to start"
    irserver_status
}

irserver_stop() { killall $FNAME }

#irserver_reload() {
#        if [[ $(mount | grep -c ${MNT}) > 0 ]]; then
#                echo "Unmounting ${MNT}"
#                umount ${MNT}
#        fi
#        kill -HUP `cat ${PID}` >&/dev/null
#
#        echo "Mounting ${MNT}"
#        sleep 5
#        mount ${MNT}
#        if [[ $? != 0 ]]; then
#                echo "Failed to start jungle disk"
#        fi
#}

irserver_status() {
        TEMPPID=`ps -A | grep irserver | grep -v 'bash\|grep\|mount' | awk '{ print $1 }'`
        if [ "${TEMPPID}" > 0 ]; then
                echo "Running on PID: $TEMPPID"
        else
                echo "Not running"
        fi
}

case $1 in
        start)
                echo "Starting $NAME"
                irserver_start
                exit 0
        ;;
        stop)
                echo "Stopping $NAME"
                irserver_stop
                exit 0
        ;;
#        reload)
#                echo "Reloading $NAME"
#                irserver_reload
#                exit 0
#        ;;
        status)
                irserver_status
                exit 0
        ;;
        *)
                echo "Usage: /etc/init.d/irserver start|stop|status" >&2
                exit 0
        ;;
esac
}
```

The program is located at /usr/local/irtrans/irserver64, is that file correct?

I tried adding it to startup with "sudo update-rc.d startir 97 2 3 4 5 . "

The daemon doesn't start.  I also did chmod 766 startir to make sure it was executable.

How do I make sure that it's starting?  Is there a log I can view that will tell me about errors?  How can I check if it's running?

---

