---
title: "Autostart VNC-server"
date: 2005-08-05
forum: Absolute Beginner Talk
---

### Post by mikuskuikku on 2005-08-05
Hi all! (This is my first post)

Question:
In Redhat there was a configuration file that let me autostart programs and services automaticly when the computer was started.
How can I do this in Ubuntu?

I need to start VNC-server before/after GDM (login-screen) starts so that I can do a login with my VNC-viewer.

Any 'autostart' configuration is helpful.

<<Mika>>

---

### Post by manicka on 2005-08-05
System-->Preferences-->Sessions

Go to the Startup Programs Tab

---

### Post by mikuskuikku on 2005-08-05
[QUOTE=manicka]System-->Preferences-->Sessions

Go to the Startup Programs Tab[/QUOTE]

But i need to get the program started without anybody logging in to UBUNTU.
The computer starts automaticly (power on) without anybody standing by it. So I need the VNC-server to start so that I can do the logging in.
Is this the cas with 'System > Preferences > Sessions'?
<<Mika>>

---

### Post by manicka on 2005-08-05
[QUOTE=mikuskuikku]
Is this the cas with 'System > Preferences > Sessions'?
<<Mika>>[/QUOTE]

No, it's not.

Sorry, I can't help you with what you need to do.  :| 

Maybe this will bump it up and someone else with know :)

---

### Post by Sam on 2005-08-06
This looks like a big hack, but edit the file /etc/init.d/gdm, then add the command you need in the start and stop case:

```
<snip />
case "$1" in
  start)
  	# START VNC HERE
  	if [ -e "$DEFAULT_DISPLAY_MANAGER_FILE" -a "$HEED_DEFAULT_DISPLAY_MANAGER" = "true" -a "$(cat $DEFAULT_DISPLAY_MANAGER_FILE)" != "$DAEMON" ]; then
		log_warning_msg "Not starting GNOME Display Manager (gdm); it is not the default display manager."
	else
		log_begin_msg "Starting GNOME Display Manager..."
		start-stop-daemon --start --quiet --pidfile $PIDFILE --name gdm $SSD_ARG >/dev/null 2>&1 || log_end_msg 1
		log_end_msg 0
	fi
  ;;
  stop)
  	# STOP VNC HERE
	log_begin_msg "Stopping GNOME Display Manager..."
	start-stop-daemon --stop  --quiet --pidfile $PIDFILE --name gdm $SSD_ARG --retry 30 >/dev/null 2>&1 || \
		log_success_msg "GNOME Display Manager not running"
	log_end_msg 0
  ;;
  reload)
  	# STOP VNC HERE
  	# START VNC HERE
	log_begin_msg "Reloading GNOME Display Manager configuration..."
	log_warning_msg "Changes will take effect when all current X sessions have ended."
	start-stop-daemon --stop --signal USR1 --quiet --pidfile \
		$PIDFILE --name gdm $SSD_ARG >/dev/null 2>&1
	log_end_msg 0
  ;;
  restart|force-reload)
	$0 stop || true
	$0 start
  ;;
  *)
	log_success_msg "Usage: /etc/init.d/gdm {start|stop|restart|reload|force-reload}"
	exit 1
  ;;
esac
<snip />

```

Or you can create your own init.d function.....

---

### Post by Elijah on 2005-08-06
I curious on how this is done in ubunto myself so I did a search ... : 

[http://ubuntuforums.org/archive/index.php/t-12071.html](http://ubuntuforums.org/archive/index.php/t-12071.html) , it's for autostarting a script in /etc/init.d/, it's not for vnc btw.

---

### Post by jdbg on 2007-06-09
Hi,

I have a question about that too.
I need to have the Remote Desktop started on my server before the login so that I can login on to it. What commands I have to add in the /etc/init.d/ ?

thanks in advance

---

### Post by tmcmulli on 2007-09-05
Is there any way to see all the services that currently get started on boot?  A little off subject, but if I know that, I can figure out how to add/remove from that list.

---

### Post by ABX on 2007-10-16
I'd like to know that too.

I have experimented with Ubuntu a lot and now I have many services I'd like to set to manual.
I there any "services.msc" application like it is in windows, where I can configure the startup option?

---

### Post by themorningflight on 2008-03-24
I searched these forums for help with getting vnc to auto-start on my server without a monitor connected. I wanted to be able to reboot my machine from a distance. 

I eventually discovered it was easier than I had thought. Go to my blog [TheMorningFlight]("http://themorningflight.com/index.php/2008/03/24/auto-start-vnc-on-server/") for the step by step how-to.

I now have my own server running Ubuntu that I can use for backup or to access files and documents wherever I have internet access.

Have fun.

---

### Post by papasi on 2008-06-15
add this in /etc/rc.local (before exit 0)

sudo -b -H -u your_username /usr/bin/vncserver

---

