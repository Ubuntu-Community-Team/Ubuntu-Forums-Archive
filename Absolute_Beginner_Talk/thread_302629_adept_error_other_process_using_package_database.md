---
title: "adept error: other process using package database"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by ridgeback on 2006-11-18
I had a problem with Adept Installer.  I was installing a lot of things, including some Java packages, one of which needed console input, as described by "show details."  I helped it along, but the terminal emulator froze so I quit Adept, eventually by force.  Now when I try to run Adept again to finish installing the applications, I get the following error:

Another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one.

I am not aware of any other application using the package database, and it is probably because of the first Adept crash.  How can I release the packaging system database so Adept can use it again?  Or, how do I view all running processes so I can manually terminate whichever is still using it?  Thanks in advance for some help for a 2 day old linux user...

---

### Post by loell on 2006-11-18
have your tried restarting it?

---

### Post by jordanmthomas on 2006-11-18
try these:
```
sudo killall dpkg
sudo killall adept
sudo killall apt
sudo killall aptitude

```
After killing off everything that could be using your file, you should be able to restart adept


**note, this will probably make you have to run this afterwards:
```
sudo apt-get -f install
```


to view all your processes (as requested)
```
 ps -A
```
and to search for a certain process
```
 ps -A | grep process
```
then, you can use 
```
 kill *process id*
```
or
```
killall process
```

---

### Post by ridgeback on 2006-11-18
I tried everything listed, and I am on a fresh restart, and I get the same error when trying to open Add/Remove Programs.

---

### Post by jordanmthomas on 2006-11-18
In that case, a lock got left in place, and you'll have to manually remove it.
```
sudo rm /var/cache/apt/archives/lock
```
See if that helps any.

---

### Post by ridgeback on 2006-11-18
Still have the same error...

---

### Post by jordanmthomas on 2006-11-18
Try running this from a command line and see what it complains about.  If it is a locked file, find it and remove it.
```
sudo apt-get update
```

This is strange, you should be up and running by now...

---

### Post by ridgeback on 2006-11-18
There is an Add/Remove Applications in the lost and found, which I assume uses the package database, that opens but any changes cause the following error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

Might this have something to do with it? I couldn't figure out how to run dpkg --configure -a or where to run it from.  Hope this new information will help someone help me solve my problem... Thanks...

---

### Post by jordanmthomas on 2006-11-18
Ahh, that's easy to fix.
```
sudo dpkg --configure -a
```
just like it says.  I should have thought of that sooner.  *doh*

---

### Post by ridgeback on 2006-11-18
I must have forgotten the sudo.  Problem solved! Thanks a ton for all your help!

---

### Post by jordanmthomas on 2006-11-18
sorry it took so long, but glad it's fixed.

---

### Post by binks on 2006-11-21
i have the same problem but 
sudo dpkg --configure -a
gives me n error 
/etc/init.d/freeradius: 15: source: not found
invoke-rc.d: initscript freeradius, action "reload" failed.
dpkg: error processing freeradius-mysql (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 freeradius-mysql
binks@binks-desktop:~$ sudo dpkg --configure -a
Setting up freeradius-mysql (1.1.3-1) ...
/etc/init.d/freeradius: 15: source: not found
invoke-rc.d: initscript freeradius, action "reload" failed.
dpkg: error processing freeradius-mysql (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 freeradius-mysql



any ideas please 
binks

---

### Post by jordanmthomas on 2006-11-21
Have you installed freeradius?
It seems as though its script to start and stop iteself is missing.  You can get it directly from the package.  For your convenience, I have gone and fetched the script for you:
```
#!/bin/sh
# Start/stop the FreeRADIUS daemon.

set -e

source /lib/lsb/init-functions

PROG="freeradius"
PROGRAM="/usr/sbin/freeradius"
PIDFILE="/var/run/freeradius/freeradius.pid"
DESCR="FreeRADIUS daemon"

test -f $PROGRAM || exit 0

# /var/run may be a tmpfs
test -d /var/run/freeradius || {
	mkdir -p /var/run/freeradius
	chown freerad:freerad /var/run/freeradius
}

case "$1" in
	start)
#		echo -n "Starting $DESCR: "
		log_daemon_msg "Starting $DESCR" "$PROG"
		start-stop-daemon --start --quiet --pidfile $PIDFILE --exec $PROGRAM
		if [ $? = 0 ]; then
#			echo "$PROG."
			log_end_msg 0
		else
#			echo "(failed!  run '$PROGRAM -x' to find out why.)"
			log_end_msg 1
			exit 1
		fi
		;;
	stop)
#		echo -n "Stopping $DESCR: "
		log_daemon_msg "Stopping $DESCR" "$PROG"
		start-stop-daemon --stop --quiet --pidfile $PIDFILE
#		echo "$PROG."
		log_end_msg 0
		;;
	restart)
#		echo -n "Restarting $DESCR: "
		$0 stop
		sleep 2
		$0 start
		;;
	reload | force-reload) 
#		echo -n "Reloading configuration files for $DESCR"
		log_action_begin_msg "Reloading configuration files for $DESCR"
		start-stop-daemon --stop --signal 1 --quiet --pidfile $PIDFILE
		log_action_cont_msg "HUP sent"
		sleep 2
#		ps --pid $(cat $PIDFILE) > /dev/null || exit 1
		ps --pid $(cat $PIDFILE) > /dev/null
		if [ $? = 0 ]; then
			log_action_end_msg 0
		else
			log_action_end_msg 1 "$DESCR died"
			exit 1
		fi
#		echo "."
		;;
	*)
		echo "Usage: /etc/init.d/freeradius start|stop|restart|reload|force-reload"
		exit 1 
esac

exit 0

```

Type on a command line:
```
sudo su
nano /etc/init.d/freeradius

```
Select the text above, and middle click / paste it into nano.
Ctrl-O,Ctrl-X to save and exit
```

chmod +x /etc/init.d/freeradius # make it executable
exit
```
to leave your root console and go back to being you.
```
sudo dpkg --configure -a
```
See if that helps any.

---

### Post by KarlXII on 2007-01-05
Here's my working solution to the adept lock file prob: [http://www.ubuntuforums.org/showthread.php?t=331923](http://www.ubuntuforums.org/showthread.php?t=331923)

---

### Post by Thundar_2001 on 2007-10-19
Alright, so I had this problem, but every time I tried to do ```
sudo dpkg --configure -a
```it would lock me out of that, too (saying "dpkg: status database area is locked by another process"). So I combined this solution with the one above (removing lock files, specifically the one from dpkg) by ```
sudo rm /var/lib/dpkg/lock
```first. Hope this helps someone else who has the same issue I had.

---

### Post by BestMan10 on 2008-04-08
> **jordanmthomas said:**
> Ahh, that's easy to fix.
```
sudo dpkg --configure -a
```
just like it says.  I should have thought of that sooner.  *doh*

Thank you too much it was fixed my problem.:lolflag:

---

