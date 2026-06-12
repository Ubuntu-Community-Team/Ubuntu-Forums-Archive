---
title: "How to use init.d?!"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by jrsutton on 2007-11-23
I am new to Linux and am trying to use a "real world problems" to learn from. I decided I wanted to host a ventrilo server for my friends and I. I installed ventrilo here: "/Public/Ventrilo/ventsrv" Once the server was running I decided to create it as a service. I have done a lot of reading via google and these forums, and here is what I have accomplished so far:

I have saved this script below as ventrilo to /etc/init.d then ran sudo chmod +x ventrilo.
I then tested the script via ./ventrilo start, stop, etc...
After this I typed runlevel then did cd ../rc2.d and used ```
ln -s /etc/init.d/ventrilo S99ventrilo
```
With the symbolic link created I performed a restart and sure enough before I logged in, the vent server was up and running. Now my problem is, when I perform a shutdown and as everything is shutting down "Starting Ventrilo Server" is displayed on the screen then my PC shuts off. How do I correctly add a symbolic link to properly shut down the vent server? I'm assuming I should add the symbolic links to rc0.d rc1.d and rc6.d. But do I need a different script for this? What is the proper way to cleaning shut down the app when shutting down my PC?
```

#!/bin/sh
VENTRILO_DIR=/home/me/Public/Ventrilo/ventsrv
VENTRILO_USER=me
cd $VENTRILO_DIR
case "$1" in
start)
if [ -e ventrilo_srv.pid ]
then
echo "Ventrilo Server Is Already Running"
else
echo "Starting Ventrilo Server"
su $VENTRILO_USER -c './ventrilo_srv -d'
echo "Ventrilo Server Started"
fi
;;
stop)
if [ -e ventrilo_srv.pid ]
then
echo "Shutting Down Ventrilo Server"
kill `cat ventrilo_srv.pid`
echo "Ventrilo Server Shutdown"
else
echo "Ventrilo Server Not Running";
fi
;;
restart)
echo "Restarting Ventrilo Server"
if [ -e ventrilo_srv.pid ]
then
echo "Shutting Down Ventrilo Server"
kill `cat ventrilo_srv.pid`
else
echo "Ventrilo Server Not Running";
fi
echo "Starting Ventrilo Server"
su $VENTRILO_USER -c './ventrilo_srv -d'
echo "Ventrilo Server Restarted"
;;
status)
if [ -e ventrilo_srv.pid ]
then
echo "Ventrilo Server Is Running"
else
echo "Ventrilo Server Is Stopped"
fi
;;
*)
echo "Usage: $0 (start|stop|restart|status)"
exit 1
esac
exit 0

```

---

### Post by scxtt on 2007-11-23
for your shutdown runlevel(s) you want to use something like K99ventrilo instead of S99ventrilo ...

---

### Post by jrsutton on 2007-11-23
So I should run
```
ln -s /etc/init.d/ventrilo K99ventrilo
```
In each of these directories?
rc0.d
rc1.d
rc6.d

I guess I don't understand how it knows to shut the app down using the same script?

---

### Post by scxtt on 2007-11-23
i can't say for 100%, but basically the idea is S=start K=stop ... so, **ln -s /etc/init.d/ventrilo K99ventrilo** should work fine if you're in any runlevel you want the link to live in ... it's basically like saying **/etc/init.d/ventrilo stop** ...

put it in the rc*.d directories where the system shuts down or reboots ... not all flavors use the various runlevels the same, and i can't remember what they are in ubuntu ...

i'd say rc0.d is SHUTDOWN and rc6.d is REBOOT ...

rc1.d is for "single user mode" ...

---

### Post by nick_h on 2007-11-24
Can you make use of the update-rc.d command?

There is a man page for details:
```
man update-rc.d
```

---

### Post by jrsutton on 2007-11-24
I originally used the update command but it just puts it in all the rc folders. This to me seems sloppy. Maybe I don't understand enough or it. If I use ln -s with the rc directory I want to put it in, then use the update-rc.d it tells me the links already exists.

---

### Post by nick_h on 2007-11-24
update-rc.d will exit if you have already set up some links.  This is so that it doesn't reconfigure a customised service.

With the defaults, it will add links to start the service in run levels 2,3,4 and 5; it will also add links to stop the service in run levels 0,1 and 6.

---

