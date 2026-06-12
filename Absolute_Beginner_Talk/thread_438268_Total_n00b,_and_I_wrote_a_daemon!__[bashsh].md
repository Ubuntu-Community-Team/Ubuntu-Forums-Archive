---
title: "Total n00b, and I wrote a daemon!  [bash/sh]"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by sudo_nym on 2007-05-09
Check this out, I've only been using Xubuntu for a couple months now.

Okay, it's just a simple loop script, and probably insecure as hell [uses a world-writable directory to take instructions from the user], but that's okay for me because FTP is the *only* network service I have running, and even that's usually turned off [handy for transferring files between Linux / Mac / PC though].  And it's all behind a router.

But the neat thing about this is, I can turn FTP on and off with a launcher button now, without getting hassled for a password every time.  That and a few other things.

Don't know if I can call it a daemon really, because there is a little bit of user interaction here.  Nothing fancy, just a couple of notification popups.

Anyway, here's /usr/local/r00t_l00p , usually called from an automatic `gksu r00t_l00p' command at login;

```
#!/bin/sh

echo Starting r00t_l00p...

#  This script adds some super-user functionality to regular
#  old Wendy Whitebread accounts.
#
#  What it does is check for certain directory names in /tmp,
#  then acts on whatever it finds there.  So other programs, and
#  the user, can communicate with it via `mkdir' or a launcher
#  button containing a simple `mkdir /tmp/r00t/whatever' command.

mkdir -p /tmp/r00t/run
sleep 11
rm -rf /tmp/r00t/run
#
#  If the `run' folder exists, this indicates that a r00t script has
#  just been started, so other instances should quit now.
#
#  Stops multiple instances piling up from one login to the next.

chmod -R 777 /tmp/r00t


while :
do
	if [ -x /tmp/r00t/run ]
	then
		echo Ending r00t_l00p.
		exit 0



	elif [ -x /tmp/r00t/shutdown ]
	####  Unused, but I might need these sometime...
	then
		rm -rf /tmp/r00t/shutdown
		killall sleep
		sudo -u moi xmms -s
		sleep 2
		shutdown -P now "Thassal, Folks!"

	elif [ -x /tmp/r00t/reboot ]
	then
		rm -rf /tmp/r00t/reboot
		killall sleep
		sudo -u moi xmms -s
		sleep 2
		reboot



	elif [ -x /tmp/r00t/hibernate ]
	####  But I do need this, because the standard
	####  `Hibernate' button never works in Xubuntu...
	then
		rm -rf /tmp/r00t/hibernate
		sudo -u moi xmms -s
		sleep 2
		umount /dev/sda1

		/etc/acpi/hibernate.sh
		#
		#  Requires the addition of an `&' in
		#  /etc/acpi/hibernate.sh
		#
		#  Here, on the last line;
		#  . /etc/acpi/resume.sh &
		#
		#  Otherwise, the hibernate script will just sit there
		#  and wait, long after it's finished its work.  And so
		#  will r00t_l00p; waiting for hibernate.sh to exit.

		#  And on resume;
		#
		sudo -u moi mount /dev/sda1
		mount /dev/sda1
		sleep 7
		sudo -u moi xmms -p



	elif [ -x /tmp/r00t/now ]
	####  Makes `sleep'-deferred actions happen immediately
	then
		rm -rf /tmp/r00t/now
		killall sleep



	elif [ -x /tmp/r00t/ftp-switch ]
	####  Turn the server on or off
	then
		rm -rf /tmp/r00t/ftp-switch

		if [ -x /tmp/r00t/ftp-on ]
		####  If it's on, stop it
		then
			xterm -title '::0FF::' \
			-geometry 28x6 -e 'echo && echo \
			"    Stopping FTP Server." && echo && echo \
			"     [press any key to " && echo -n \
			"       close window]       " && read -n 1' &
			#
			#  Woohoo!  GUI notification dialogs
			#  from a shell script!

			rm -rf /tmp/r00t/ftp-on
			mkdir -p /tmp/r00t/ftp-off

			/etc/init.d/proftpd stop
			/etc/init.d/proftpd force-stop
			sleep 3
			killall -s 9 proftpd

		elif [ -x /tmp/r00t/ftp-off ]
		####  If it's off, start it
		then
			xterm -title '::0N::' \
			-geometry 28x6 -e 'echo && echo \
			"    Starting FTP Server." && echo && echo \
			"     [press any key to " && echo -n \
			"       close window]       " && read -n 1' &

			rm -rf /tmp/r00t/ftp-off
			mkdir -p /tmp/r00t/ftp-on

			/etc/init.d/proftpd start

		elif [ -x /tmp/r00t ]
		####  And if you don't know, stop it anyway
		then
			mkdir -p /tmp/r00t/ftp-off

			/etc/init.d/proftpd stop
			/etc/init.d/proftpd force-stop
			sleep 3
			killall -s 9 proftpd
		fi
	fi

sleep 3
done

echo Ending r00t-l00p.
exit 0
```

Oh, and about all the `xmms -s' stuff; have you ever forgotten to stop your MP3 player before hibernating?  When resuming later, the sound-card tends to wake up *before* the volume settings kick in, and it'll blow your ears of.  Not at all musical either; just choppy blasts of noise and silence until everything's done loading.  Or maybe that's just a Compaq Armada quirk...

Also, XMMS often forgets to save its playlists, unless you stop playback before quitting.

Thanks, done bragging now.



Patrick.

---

### Post by duglaswb on 2007-05-11
you rock

---

