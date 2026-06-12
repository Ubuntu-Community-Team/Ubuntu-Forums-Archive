---
title: "How to start samba service at boot up ?"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by chrisdee on 2006-09-04
Hello. Iv been searching high and low for instructions on how to make samba start automatically at boot. After each boot i have to manualy start the samba (smbd) service by running /etc/ini.d/samba start. 

Iv been searching for a long time now on how to automatically to start samba after a reboot. Would apreciate if someone could tell me how to do this.

I run Linux Ubuntu 2.6.12-10-386

Reguards

---

### Post by chrisdee on 2006-09-04
Anybody ?

---

### Post by xander848 on 2006-09-04
Go to System > Prefs > Sessions > Startup Programs

Then click add and type the command there. That should work (I think)

---

### Post by chrisdee on 2006-09-04
Thanks for the advice but that did not work for me.

---

### Post by kh4nh on 2006-09-05
Hi,

- save this in a file, call it "samba"

```

#!/bin/sh
#
# Start/stops the Samba daemons (nmbd and smbd).
#
#

# Defaults
RUN_MODE="daemons"

# Reads config file (will override defaults above)
[ -r /etc/default/samba ] && . /etc/default/samba

PIDDIR=/var/run/samba
NMBDPID=$PIDDIR/nmbd.pid
SMBDPID=$PIDDIR/smbd.pid

# clear conflicting settings from the environment
unset TMPDIR

# See if the daemons are there
test -x /usr/sbin/nmbd -a -x /usr/sbin/smbd || exit 0

. /lib/lsb/init-functions

case "$1" in
	start)
		log_daemon_msg "Starting Samba daemons..."

		# Make sure we have our PIDDIR, even if it's on a tmpfs
		install -o root -g root -m 755 -d $PIDDIR

		if ! start-stop-daemon --start --quiet --oknodo --exec /usr/sbin/nmbd -- -D; then
			log_end_msg 1
			exit 1
		fi

		if [ "$RUN_MODE" != "inetd" ]; then
			#log_progress_msg "smbd"
			if ! start-stop-daemon --start --quiet --oknodo --exec /usr/sbin/smbd -- -D; then
				log_end_msg 1
				exit 1
			fi
		fi

		log_end_msg 0
		;;
	stop)
		log_daemon_msg "Stopping Samba daemons..."

		start-stop-daemon --stop --quiet --pidfile $NMBDPID
		# Wait a little and remove stale PID file
		sleep 1
		if [ -f $NMBDPID ] && ! ps h `cat $NMBDPID` > /dev/null
		then
			# Stale PID file (nmbd was succesfully stopped),
			# remove it (should be removed by nmbd itself IMHO.)
			rm -f $NMBDPID
		fi

		if [ "$RUN_MODE" != "inetd" ]; then
			#log_progress_msg "smbd"
			start-stop-daemon --stop --quiet --pidfile $SMBDPID
			# Wait a little and remove stale PID file
			sleep 1
			if [ -f $SMBDPID ] && ! ps h `cat $SMBDPID` > /dev/null
			then
				# Stale PID file (nmbd was succesfully stopped),
				# remove it (should be removed by smbd itself IMHO.)
				rm -f $SMBDPID
			fi
		fi

		log_end_msg 0

		;;
	reload)
		log_daemon_msg "Reloading /etc/samba/smb.conf..."

		start-stop-daemon --stop --signal HUP --pidfile $SMBDPID

		log_end_msg 0
		;;
	restart|force-reload)
		$0 stop
		sleep 1
		$0 start
		;;
	*)
		log_success_msg "Usage: /etc/init.d/samba {start|stop|reload|restart|force-reload}"
		exit 1
		;;
esac

exit 0


```

- move "samba" to /etc/init.d

```

sudo mv samba /etc/init.d

```

- put symbolic links to the file "/etc/init.d/samba" in appopriate rc.* folders

```


ln -s /etc/init.d/samba /etc/rc0.d/K19samba
ln -s /etc/init.d/samba /etc/rc1.d/K19samba
ln -s /etc/init.d/samba /etc/rc1.d/K19samba

ln -s /etc/init.d/samba /etc/rc2.d/S20samba
ln -s /etc/init.d/samba /etc/rc3.d/S20samba
ln -s /etc/init.d/samba /etc/rc4.d/S20samba
ln -s /etc/init.d/samba /etc/rc5.d/S20samba


```


Hopefully this helps in some way

---

### Post by gurubaysoft on 2006-12-14
> **chrisdee said:**
> Hello. Iv been searching high and low for instructions on how to make samba start automatically at boot. After each boot i have to manualy start the samba (smbd) service by running /etc/ini.d/samba start. 

Iv been searching for a long time now on how to automatically to start samba after a reboot. Would apreciate if someone could tell me how to do this.

I run Linux Ubuntu 2.6.12-10-386

Reguards

Hi chrisdee

did u try "update-rc.d" command. for eg.
# update-rc.d samba defaults 20 21  <enter>
  should set samba services startup in default run levels automatically or for particular init level   u may try the settings with help for udate-rc.d

-guru

---

### Post by Hasen_A on 2007-01-02
> ln -s /etc/init.d/samba /etc/rc2.d/S20samba

what are the different rc?.d folders good for and why place a link in various places and not only in one?

I've also checked and all 8 softlinks already exist. With which command can I check if the samba server is running correctly?

Thanks
Andy

---

### Post by bluefrog on 2007-01-02
in console
sudo /etc/init.d/samba start       (could be smb instead of samba  though, check what's inside /etc/init.d)

test your smb.conf before by issuing in console
testparm


then just read the various error messages and correct accordingly.

James

---

### Post by mike4ubuntu on 2007-01-03
Supposedly, in Edgy, there is a new event driven subsystem that provides a better way of handling services called upstart, but I don't know exactly how it works.  

 You can see reference to it here:
[Service Upstart]("http://upstart.ubuntu.com/")

However, the /etc/init.d still works in Edgy.

---

