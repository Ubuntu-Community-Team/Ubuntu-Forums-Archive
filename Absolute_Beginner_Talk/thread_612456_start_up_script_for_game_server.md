---
title: "start up script for game server"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by jrsutton on 2007-11-13
I'm new to linux and I am trying to use this startup script to help learn. I have already installed srcds and am using this startup script to have it run prior to me logging in. The script does start the server, but does not correctly check if there is already an instance started, and my understanding is that it should.

```
# The user that will run the server
CS_USER=me

# Leave this alone.
NAME=srcds

PATH=/bin:/usr/bin:/sbin:/usr/sbin

# DON'T FORGET TO CHANGE THE PATH TO YOUR NEEDS!
DIR=/home/me/Public/srcds

# Leave this alone.
DAEMON=srcds_run

# Internet-server:
PARAMS="-console -game cstrike -tickrate 100 +fps_max 300 +maxplayers 11 -port 27015 +map de_dust2 +sv_pure 2 +mp_dynamicpricing 0 +exec server.cfg -autoupdate"

# Leave this alone.
DESC="Counter-Strike Source Dedicated Server"

case "$1" in
 start)
    [COLOR="Red"]if [[ `su $CS_USER -c "screen -ls |grep $NAME"` ]]
       then
       echo "$DESC is already running"
    else 
       echo "Starting $DESC: $NAME"
       su $CS_USER -c "cd $DIR; screen -m -d -S $NAME ./$DAEMON $PARAMS" [/COLOR][COLOR="Blue"]#This is executed no matter if an instance is already running, I can't figure out why![/COLOR]
    fi
    ;;

 stop)
    if [[ `su $CS_USER -c "screen -ls |grep $NAME"` ]]
       then
       echo -n "Stopping $DESC: $NAME"
       kill `ps aux | grep -v grep | grep -i $CS_USER | grep -i screen | grep -i $NAME | awk '{print $2}'`
       echo " ... done."
    else
       echo "Coulnd't find a running $DESC"
    fi
    ;;

 restart)
    if [[ `su $CS_USER -c "screen -ls |grep $NAME"` ]]
       then
       echo -n "Stopping $DESC: $NAME"
       kill `ps aux | grep -v grep | grep -i $CS_USER | grep -i screen | grep -i $NAME | awk '{print $2}'`
       echo " ... done."
    else
       echo "Coulnd't find a running $DESC"
    fi
   
    echo -n "Starting $DESC: $NAME"
    su $CS_USER -c "cd $DIR; screen -m -d -S $NAME ./$DAEMON $PARAMS"
    echo " ... done."
    ;;

 status)
    ps aux | grep -v grep | grep $DAEMON > /dev/null
    CHECK=$?
    [ $CHECK -eq 0 ] && echo "$DESC is UP" || echo "$DESC is DOWN"
    ;; 
 *)
    echo "Usage: $0 {start|stop|status|restart}"
    exit 1
    ;;
esac

exit 0
```

me@you:/etc/init.d$ ./hlds start
Password: 
./hlds: 116: [[: not found [COLOR="Red"]<--- I always get this error and I can't figure out why![/COLOR]
Starting Counter-Strike Source Dedicated Server: srcds
Password: 
me@you:/etc/init.d$

---

