---
title: "giFT Daemon Start on boot!"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2006-10-10
Does anyone know how to make giftd start on boot?

---

### Post by blendmaster on 2006-10-10
Click System >> Preferences >> Sessions, then click startup programs, and choose add. Put the file's directory in the box (if you don't know it, browse), and you're done!

---

### Post by guysmiley25 on 2006-10-11
Oh sorry I should of mentiond that it was running on a ubuntu-server with no gui. But thanks anyways it helped me to get amsn working on boot. I wonder if all that does is creates a script and puts it somewhere?

A problem with what I am trying to do could be that I want to run giftd as a curtain user (not root) with out logining in, just when the computer boots. it is a daemon so you dont have to be loged in for it to run by for the mean time every time i reboot my server for some reason I have to remeber to login and start it again witch is a pain.

Any one got any ideas?

---

### Post by mozetti on 2006-10-11
From what I know (still new & learning), it needs to be inserted into the init.d process that runs everything to get Ubuntu/Linux to the login screen. I think the process/commands are the same for any program you want to add to the boot-up process, but I unfortunately don't know it. It's a fairly regular task, so someone should be by here soon with the answer you (and I) would like. :)

---

### Post by guysmiley25 on 2006-10-11
Yeah I was thinking it would be somthing like that but when I went in there a opend some of them up to have a clue on what to do it was quite confusing. However as for running as a user should not be a problems becasue I found that boinc runs as a user and it have a inid script thing. But now my question is how do you write thoses scripts? what language is it? where do I go to learn some stuff about it?

---

### Post by skymt on 2006-10-11
Init scripts are just shell scripts. There's a file at /etc/init.d/skeleton that gives an example. Copy it, edit it (for start, you just want "giftd", for stop "killall giftd"), and add links in /etc/rc2.d, rc6.d, and rc0.d.

---

### Post by guysmiley25 on 2006-10-11
Ok so I have started to make a init script for the giftd deamon. I am working with the skeleton script and this is where I have got to so far. I am being assited by this [gudie]("http://developer.novell.com/wiki/index.php/Writing_Init_Scripts") and this is what ive got so far. Witch is not very much at all. Where do I go from here? Where do I put "giftd" for start and ""killall giftd" for stop? also how do I make sure that it is running as a certain user? and finaly what is this PID stuff?

```

#! /bin/sh
### BEGIN INIT INFO
# Provides:          giFTd
# Required-Start:    network
# Required-Stop:
# Default-Start:     3 5
# Default-Stop:      0 1 2 6
# Short-Description: Starts the giftd daemon
### END INIT INFO
#
# Author:	guysmiley25 (Ubuntu Fourms Member)
#
# Version:	1
#

# This line is here becasue
# a guide said so! Is it Needed?
test -s /etc/rc.status && . /etc/rc.status && rc_reset

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DESC="giFT Daemon"
NAME=giftd
DAEMON=/usr/bin/$NAME
PIDFILE=/var/run/$NAME.pid
SCRIPTNAME=/etc/init.d/$NAME

# Gracefully exit if the package has been removed.
test -x $DAEMON || exit 0

#	Function that starts the daemon/service.
#
d_start() {
	start-stop-daemon --start --quiet --pidfile $PIDFILE \
		--exec $DAEMON \
		|| echo -n " already running"
}

#
#	Function that stops the daemon/service.
#
d_stop() {
	start-stop-daemon --stop --quiet --pidfile $PIDFILE \
		--name $NAME \
		|| echo -n " not running"
}

#
#	Function that sends a SIGHUP to the daemon/service.
#
d_reload() {
	start-stop-daemon --stop --quiet --pidfile $PIDFILE \
		--name $NAME --signal 1
}

case "$1" in
  start)
	echo -n "Starting $DESC: $NAME"
	d_start
	echo "."
	;;
  stop)
	echo -n "Stopping $DESC: $NAME"
	d_stop
	echo "."
	;;
  #reload)
	#
	#	If the daemon can reload its configuration without
	#	restarting (for example, when it is sent a SIGHUP),
	#	then implement that here.
	#
	#	If the daemon responds to changes in its config file
	#	directly anyway, make this an "exit 0".
	#
	# echo -n "Reloading $DESC configuration..."
	# d_reload
	# echo "done."
  #;;
  restart|force-reload)
	#
	#	If the "reload" option is implemented, move the "force-reload"
	#	option to the "reload" entry above. If not, "force-reload" is
	#	just the same as "restart".
	#
	echo -n "Restarting $DESC: $NAME"
	d_stop
	# One second might not be time enough for a daemon to stop, 
	# if this happens, d_start will fail (and dpkg will break if 
	# the package is being upgraded). Change the timeout if needed
	# be, or change d_stop to have start-stop-daemon use --retry. 
	# Notice that using --retry slows down the shutdown process somewhat.
	sleep 1
	d_start
	echo "."
	;;
  *)
	echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload}" >&2
	exit 3
	;;
esac

exit 0

```

**Edit:** Also I have been searching to see if someone has already done this but with no such luck. This concers me a little bit. Is it just cause it is not worth the effort or because it is not possible? I really wish that gift came with this but it makes sence for it not to becasue most people would only want there gift daemon to be running when there running there app (apollon or whatever). Anyone got any thoughs?

---

### Post by guysmiley25 on 2006-10-11
OK so here is the lastest.

```

#! /bin/sh
### BEGIN INIT INFO
# Provides:          giFTd
# Description:       Starts the giftd daemon
### END INIT INFO
#
# Author:	guysmiley25 (Ubuntu Fourms Member)
#
# Version:	1
#

# This line is here becasue
# a guide said so! Is it Needed?
test -s /etc/rc.status && . /etc/rc.status && rc_reset

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
NAME=giftd
USER=gift
DAEMON=/usr/bin/$NAME
SCRIPTNAME=/etc/init.d/$NAME

# Gracefully exit if the package has been removed.
test -x $DAEMON || exit 0

case "$1" in
  start)
	echo -n "Starting giFT Daemon"
	su - $USER -c DAEMON -d
	;;
  stop)
	echo -n "Stopping giFT Daemon"
	killall giftd
	;;
  reload)
	echo -n "Restarting giFT Daemon"
	killall giftd
	su - $USER -c DAEMON -d
	;;

esac

exit 0

```

Does that look right? also now wondering about how it starts. Normally to start giftd you have to run "giftd -d" so do I just add the -d part like I have?

---

### Post by guysmiley25 on 2006-10-11
Ok so now here is the lastest, it works if I just run it, now my next step is to add it to the boot process. So here it is

```

#! /bin/sh
### BEGIN INIT INFO
# Provides:          giFTd
# Description:       Starts the giftd daemon
### END INIT INFO
#
# Author:	guysmiley25 (Ubuntu Fourms Member)
#
# Version:	1
#

# This line is here becasue
# a guide said so! Is it Needed?
test -s /etc/rc.status && . /etc/rc.status && rc_reset

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
NAME=giftd
USER=gift
DAEMON=/usr/bin/$NAME
SCRIPTNAME=/etc/init.d/$NAME

# Gracefully exit if the package has been removed.
test -x $DAEMON || exit 0

case "$1" in
  start)
	su - $USER -c "$DAEMON -d"
	;;
  stop)
	killall giftd
	;;
  reload)
	killall giftd
	su - $USER -c "$DAEMON -d"
	;;

esac

exit 0

```

---

### Post by guysmiley25 on 2006-10-11
Ok first sorry for all the post!

Ok so I made that file located at

/etc/init.d/giftd

Then I did this

```

$ sudo chmod 744 /etc/init.d/giftd
$ sudo ln -s /etc/init.d/giftd /etc/rc2.d/giftd
$ sudo ln -s /etc/init.d/giftd /etc/rc6.d/giftd
$ sudo ln -s /etc/init.d/giftd /etc/rc0.d/giftd

```

then rebooted. I may not of ran the commands in that order.

This is still not working. What am I doing wrong? Is it the script itself or somthing else?

When I run ```
$ sudo /etc/init.d/giftd start/stop/restart
``` all works well.

Any Ideas?

---

### Post by skymt on 2006-10-11
Sorry I didn't mention this before: files in rc*n*.d need special names. The format is *nnL*name, where nn is a two-digit number, and L is a letter. The number specifies what point in the startup the script should be run. You want giftd to run at the end, so use 99. L can be S or K (it has to be uppercase). If it's S, the script is run as "/etc/init.d/name start". If it's K, it's run as "/etc/init.d/name stop". S is for start, K is for kill.

So:```
sudo mv /etc/rc2.d/giftd /etc/rc2.d/S99giftd
sudo mv /etc/rc0.d/giftd /etc/rc0.d/K99giftd
sudo mv /etc/rc6.d/giftd /etc/rc6.d/K99giftd
```rc2 is run on startup, rc0 is run on shutdown, and rc6 is run on reboot. The others (1 and 3-5) aren't generally used in Ubuntu.

---

### Post by guysmiley25 on 2006-10-11
Thanks very much for that. It worked perfectly

---

### Post by dmwit on 2006-10-20
These things all run as root, right?  Can I run as another user with, for example "su limiteduser"?  Or, what is the preferred way of achieving this?
~d

---

### Post by guysmiley25 on 2006-10-20
I setup this script to run as the user "gift" but yes you can change it. If it is this script your working with you can just change this line ```
USER=gift
``` with ```
USER=limiteduser
```. And I would not recommend that you just giftd as root.

If your just using this to create your own script from somthing else then you just want somthing like this ```
su - limiteduser -c yourprogram
```

Hope that helps.

---

