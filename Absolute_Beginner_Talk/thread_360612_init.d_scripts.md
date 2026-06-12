---
title: "init.d scripts"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by rogue417 on 2007-02-13
I am extremely new to Linux and Ubuntu so please forgive me for asking such a basic question;

I have a start/stop script for a milter which I have put in the /etc/init.d dir.  I called it dkfilter sense it should start/stop dkfilter.  The problem is I dont know what extension to give it or how to cignify that it is a scrip.  I try running dkfilter start and get the following error.

-bash: dkfilter: command not found

What do I need to do to make this scrip run.

```
#!/bin/sh
#
# Copyright (c) 2005 Messiah College.

DKFILTERUSER=dkfilter
DKFILTERGROUP=dkfilter
DKFILTERDIR=/usr/local/dkfilter

HOSTNAME=`hostname -f`
DOMAIN=`hostname -d`
DKFILTER_IN_ARGS="--hostname=$HOSTNAME 127.0.0.1:10025 127.0.0.1:10026"
DKFILTER_OUT_ARGS="--keyfile=$DKFILTERDIR/private.key --selector=postfix --domain=$DOMAIN --method=nofws --headers 127.0.0.1:10027 127.0.0.1:10028"

DKFILTER_IN_BIN="$DKFILTERDIR/bin/dkfilter.in"
DKFILTER_OUT_BIN="$DKFILTERDIR/bin/dkfilter.out"
PIDDKFILTER_IN="/var/run/dkfilter.in"
PIDDKFILTER_OUT="/var/run/dkfilter.out"

case "$1" in
	start)
		echo -n "Starting inbound DomainKeys-filter (dkfilter.in)..."
		 start-stop-daemon --start -q -p$PIDDKFILTER_IN -u $DKFILTERUSER -g $DKFILTERGROUP -x `$DKFILTER_IN_BIN $DKFILTER_IN_ARGS`
		RETVAL=$?
		if [ $RETVAL -eq 0 ]; then
			echo done.
		else
			echo failed.
			exit $RETVAL
		fi
		echo -n "Starting outbound DomainKeys-filter (dkfilter.out)..."
		 start-stop-daemon --start -q -p $PIDDKFILTER_OUT -u $DKFILTERUSER -g $DKFILTERGROUP -x `$DKFILTER_OUT_BIN $DKFILTER_OUT_ARGS` &
		RETVAL=$?
		if [ $RETVAL -eq 0 ]; then
			echo done.
		else
			echo failed.
			exit $RETVAL
		fi
		;;

	stop)
		echo -n "Shutting down inbound DomainKeys-filter (dkfilter.in)..."
		 start-stop-daemon --stop -p $PIDDKFILTER_IN
		RETVAL=$?
		if [ $RETVAL -eq 0 ]; then
			echo done.
		else
			echo failed.
		fi
		echo -n "Shutting down outbound DomainKeys-filter (dkfilter.out)..."
		start-stop-daemon --stop -p $PIDDKFILTER_OUT
		RETVAL=$?
		if [ $RETVAL -eq 0 ]; then
			echo done.
		else
			echo failed.
			exit $RETVAL
		fi
		;;
	restart)
		$0 stop
		$0 start
		;;
	*)
		echo "Usage: $0 {start|stop|restart}"
		exit 1
		;;
esac
```

---

### Post by taurus on 2007-02-13
You don't need any extension for it at all.  Just make sure it has an executable permission and you are all set to go.  Also, may want to change the first line to

```
#!/bin/bash
```

---

### Post by rogue417 on 2007-02-13
Thanks... The permissions thing got me half way there (I think).

I still can not get the script to run however.  I grabbed it from [HTML]http://www.enterux.com/files/dkfilter[/HTML] and edited it so it looks like this now:

```
#!/bin/sh
#
# Copyright (c) 2005 Messiah College.

DKFILTERUSER=dkfilter
DKFILTERGROUP=dkfilter
DKFILTERDIR=/usr/local/dkfilter

HOSTNAME=`*my.host.name* -f`
DOMAIN=`*my.host.name* -d`
DKFILTER_IN_ARGS="--hostname=$HOSTNAME 127.0.0.1:10025 127.0.0.1:10026"
DKFILTER_OUT_ARGS="--keyfile=$DKFILTERDIR/private.key --selector=postfix --domai
n=$DOMAIN --method=nofws --headers 127.0.0.1:10027 127.0.0.1:10028"

DKFILTER_IN_BIN="$DKFILTERDIR/bin/dkfilter.in"
DKFILTER_OUT_BIN="$DKFILTERDIR/bin/dkfilter.out"
PIDDKFILTER_IN="/var/run/dkfilter.in"
PIDDKFILTER_OUT="/var/run/dkfilter.out"

case "$1" in
	start)
		echo -n "Starting inbound DomainKeys-filter (dkfilter.in)..."
		 start-stop-daemon --start -q -p$PIDDKFILTER_IN -u $DKFILTERUSER -g $DKFILTERGROUP -x `$DKFILTER_IN_BIN $DKFILTER_IN_ARGS`
		RETVAL=$?
		if [ $RETVAL -eq 0 ]; then
			echo done.
		else
			echo failed.
			exit $RETVAL
		fi
		echo -n "Starting outbound DomainKeys-filter (dkfilter.out)..."
		 start-stop-daemon --start -q -p $PIDDKFILTER_OUT -u $DKFILTERUSER -g $DKFILTERGROUP -x `$DKFILTER_OUT_BIN $DKFILTER_OUT_ARGS` &
		RETVAL=$?
		if [ $RETVAL -eq 0 ]; then
			echo done.
		else
			echo failed.
			exit $RETVAL
		fi
		;;

	stop)
		echo -n "Shutting down inbound DomainKeys-filter (dkfilter.in)..."
		 start-stop-daemon --stop -p $PIDDKFILTER_IN
		RETVAL=$?
		if [ $RETVAL -eq 0 ]; then
			echo done.
		else
			echo failed.
		fi
		echo -n "Shutting down outbound DomainKeys-filter (dkfilter.out)..."
		start-stop-daemon --stop -p $PIDDKFILTER_OUT
		RETVAL=$?
		if [ $RETVAL -eq 0 ]; then
			echo done.
		else
			echo failed.
			exit $RETVAL
		fi
		;;
	restart)
		$0 stop
		$0 start
		;;
	*)
		echo "Usage: $0 {start|stop|restart}"
		exit 1
		;;
esac
```


I am obviously missing something though I have no idea what it is.  Any help would be appreciated.

Thanks!

---

### Post by taurus on 2007-02-13
Have you tried something like

```
sudo /etc/init.d/dkfilter start
```

---

### Post by rogue417 on 2007-02-13
Yeah, that is exactly what I tried.  I got the following error.

```
sudo: dkfilter: command not found
```

---

### Post by taurus on 2007-02-13
What is the name of that file that you saved?  What's the output of this command?

```
ls -la /etc/init.d
```

---

### Post by rogue417 on 2007-02-13
The file is called dkfilter.
The output is:

```
total 444
drwxr-xr-x   2 root root 4096 2007-02-13 09:44 .
drwxr-xr-x 118 root root 4096 2007-02-12 13:48 ..
-rwxr-xr-x   1 root root 2442 2005-09-15 11:30 acpid
-rwxr-xr-x   1 root root  867 2006-03-28 08:26 acpi-support
-rwxr-xr-x   1 root root 9282 2006-05-29 05:03 alsa-utils
-rwxr-xr-x   1 root root 3551 2006-01-16 08:41 amavis
-rwxr-xr-x   1 root root 1015 2005-05-02 19:10 anacron
-rwxr-xr-x   1 root root 4705 2006-07-26 11:01 apache2
-rwxr-xr-x   1 root root 1386 2005-05-23 15:15 apmd
-rwxr-xr-x   1 root root 1387 2006-05-08 14:44 atd
-rwxr-xr-x   1 root root 1109 2005-10-27 05:15 binfmt-support
-rwxr-xr-x   1 root root 2416 2006-01-18 15:11 bittorrent
-rwxr-xr-x   1 root root 5298 2006-03-19 21:52 bluez-utils
-rw-r--r--   1 root root 2553 2006-05-23 03:39 bootclean.sh
-rwxr-xr-x   1 root root 1788 2006-05-23 03:39 bootlogd
-rwxr-xr-x   1 root root 2030 2006-05-23 03:39 bootmisc.sh
-rwxr-xr-x   1 root root  881 2006-04-20 02:28 brltty
-rwxr-xr-x   1 root root 1984 2006-05-23 03:39 checkfs.sh
-rwxr-xr-x   1 root root 8831 2006-05-23 03:39 checkroot.sh
-rwxr-xr-x   1 root root 3837 2006-05-14 04:32 clamav-daemon
-rwxr-xr-x   1 root root 5469 2006-05-14 04:33 clamav-freshclam
-rwxr-xr-x   1 root root 5979 2006-01-23 08:50 console-screen.sh
-rwxr-xr-x   1 root root 1159 2006-06-08 01:27 courier-authdaemon
-rwxr-xr-x   1 root root 2267 2006-06-08 01:27 courier-imap
-rwxr-xr-x   1 root root 2535 2006-06-08 01:27 courier-imap-ssl
-rwxr-xr-x   1 root root 2172 2006-06-08 01:27 courier-pop
-rwxr-xr-x   1 root root 2606 2006-06-08 01:27 courier-pop-ssl
-rwxr-xr-x   1 root root 1739 2005-11-15 04:42 cron
-rwxr-xr-x   1 root root 1949 2006-08-03 01:52 cupsys
-rwxr-xr-x   1 root root 2557 2006-05-15 12:40 dbus
-rwxr-xr-x   1 root root 1725 2007-02-13 09:44 dkfilter
-rwxr-xr-x   1 root root  795 2006-02-23 08:37 dns-clean
-rwxr-xr-x   1 root root  923 2006-05-16 01:41 evms
-rwxr-xr-x   1 root root 1196 2006-05-21 07:44 festival
-rwxr-xr-x   1 root root 2569 2006-08-02 07:03 gdm
-rwxr-xr-x   1 root root 6175 2006-05-21 11:46 glibc.sh
-rwxr-xr-x   1 root root 1404 2006-05-23 03:39 halt
-rwxr-xr-x   1 root root 5137 2005-04-21 03:10 hdparm
-rwxr-xr-x   1 root root  992 2006-05-23 03:39 hostname.sh
-rwxr-xr-x   1 root root 2245 2006-04-29 12:09 hotkey-setup
-rwxr-xr-x   1 root root 4213 2006-04-27 05:39 hplip
-rwxr-xr-x   1 root root 3634 2006-05-15 18:43 hwclock.sh
-rwxr-xr-x   1 root root 3170 2005-11-25 12:30 keymap.sh
-rwxr-xr-x   1 root root 1840 2006-04-24 11:36 klogd
-rwxr-xr-x   1 root root 1153 2006-05-06 08:45 laptop-mode
-rwxr-xr-x   1 root root 1358 2006-05-10 17:01 lighttpd
-rwxr-xr-x   1 root root  349 2006-07-10 07:05 linux-restricted-modules-common
-rwxr-xr-x   1 root root  748 2006-01-23 10:47 loopback
-rwxr-xr-x   1 root root 2867 2005-11-08 00:30 lvm
-rwxr-xr-x   1 root root  822 2005-11-25 07:16 makedev
-rwxr-xr-x   1 root root 1124 2006-05-16 05:41 mdadm
-rwxr-xr-x   1 root root 1059 2006-05-16 05:41 mdadm-raid
-rwxr-xr-x   1 root root  921 2006-05-05 08:47 module-init-tools
-rwxr-xr-x   1 root root 2069 2006-05-23 03:39 mountall.sh
-rwxr-xr-x   1 root root 1256 2006-05-23 03:39 mountdevsubfs
-rwxr-xr-x   1 root root 1384 2006-05-23 03:39 mountvirtfs
-rwxr-xr-x   1 root root 2290 2006-05-23 03:39 mtab
-rwxr-xr-x   1 root root 4926 2006-09-05 01:51 mysql
-rwxr-xr-x   1 root root 1548 2006-09-05 01:51 mysql-ndb
-rwxr-xr-x   1 root root 1472 2006-09-05 01:51 mysql-ndb-mgm
-rwxr-xr-x   1 root root 1685 2006-05-10 23:54 networking
-rwxr-xr-x   1 root root  860 2005-10-28 19:48 nvidia-kernel
-rwxr-xr-x   1 root root 6773 2006-06-15 08:04 pcmcia
-rwxr-xr-x   1 root root 3386 2006-03-23 12:40 pcmciautils
-rwxr-xr-x   1 root root 2894 2006-06-08 01:22 postfix
-rwxr-xr-x   1 root root 1748 2006-01-18 21:33 postgrey
-rwxr-xr-x   1 root root 3629 2006-05-08 10:46 powernowd
-rwxr-xr-x   1 root root  177 2006-05-08 10:46 powernowd.early
-rwxr-xr-x   1 root root 1061 2006-07-05 06:00 ppp
-rwxr-xr-x   1 root root  281 2006-07-05 06:00 pppd-dns
-rwxr-xr-x   1 root root 1234 2006-01-23 08:10 procps.sh
-rwxr-xr-x   1 root root 6897 2006-05-23 03:39 rc
-rwxr-xr-x   1 root root  522 2006-05-23 03:39 rc.local
-rwxr-xr-x   1 root root  188 2006-05-23 03:39 rcS
-rwxr-xr-x   1 root root 1424 2006-02-24 05:31 readahead
-rwxr-xr-x   1 root root 1883 2006-02-24 05:31 readahead-desktop
-rw-r--r--   1 root root  866 2006-05-23 03:39 README
-rwxr-xr-x   1 root root  732 2006-05-23 03:39 reboot
-rwxr-xr-x   1 root root 1226 2006-05-23 03:39 rmnologin
-rwxr-xr-x   1 root root 2924 2006-05-05 07:41 rsync
-rwxr-xr-x   1 root root 1931 2007-01-03 12:05 saslauthd
-rwxr-xr-x   1 root root  452 2006-04-26 14:39 screen
-rwxr-xr-x   1 root root 1081 2006-05-23 03:39 sendsigs
-rwxr-xr-x   1 root root 1126 2006-05-23 03:39 single
-rwxr-xr-x   1 root root 2679 2006-05-23 03:39 skeleton
-rwxr-xr-x   1 root root 2016 2006-10-02 04:26 ssh
lrwxrwxrwx   1 root root    8 2006-12-27 12:32 stop-bootlogd -> bootlogd
-rwxr-xr-x   1 root root  864 2006-02-24 05:31 stop-readahead
-rwxr-xr-x   1 root root 1669 2006-04-24 11:36 sysklogd
-rwxr-xr-x   1 root root 2539 2006-05-22 07:24 udev
-rwxr-xr-x   1 root root 1588 2006-05-23 03:39 umountfs
-rwxr-xr-x   1 root root 1989 2006-05-23 03:39 umountnfs.sh
-rwxr-xr-x   1 root root  912 2006-05-23 03:39 umountroot
-rwxr-xr-x   1 root root 1965 2006-05-23 03:39 urandom
-rwxr-xr-x   1 root root 2192 2006-02-22 19:50 usplash
-rwxr-xr-x   1 root root  820 2006-06-19 03:52 vbesave
-rwxr-xr-x   1 root root 1967 2006-05-23 03:39 waitnfs.sh
-rwxr-xr-x   1 root root 1091 2006-04-24 10:53 x11-common
psnetwork@postman:/etc/init.d$
```

I set the permissions so that they are the same as all the other files around it.

Any thoughts on what is missing?

---

### Post by taurus on 2007-02-13
What about

```
ls -la /usr/local/dkfilter
```

---

### Post by rogue417 on 2007-02-13
That spits out the following.  
```
-rwxr-xr-x 1 root root 1725 2007-02-13 09:44 dkfilter
```
Would it help if I told you what I am trying to do?

---

### Post by steve.horsley on 2007-02-13
> Yeah, that is exactly what I tried. I got the following error.

Code:

sudo: dkfilter: command not found


No. Not quite right. This command:
**sudo /etc/init.d/dkfilter start**
would give you this error message:
sudo: /etc/init.d/dkfilter: command not found

It would help if you posted the command you typed as well as the output, just so we can double-check, look for extra spaces etc. e.g.
> steve@StevesPC:~$ sudo /etc/init.d/dkfilter start
sudo: /etc/init.d/dkfilter: command not found
steve@StevesPC:~$ 

From your error message, I guess you didn't type the full path to the script.


Once you have it working, you need to use this command to make dkfilter start every time you boot Ubuntu:
**sudo ln -s /etc/init.d/dkfilter /etc/rc2.d/S95dkfilter**

---

### Post by rogue417 on 2007-02-15
Ok then... I was running sudo dkfilter start in etc/init.d and figured that should work.

When I run sudo /etc/init.d/dkfilter start I get the following 

```
user@postman:~$ sudo /etc/init.d/dkfilter start
Password:
/etc/init.d/dkfilter: line 9: mail.*domain*.com: command not found
/etc/init.d/dkfilter: line 10: mail.*domain*.com: command not found
Starting inbound DomainKeys-filter (dkfilter.in)...Option hostname requires an argument
Usage:
      dkfilter.in [options] listen.addr:port talk.addr:port
        options:
          --reject-fail
          --reject-error
          --hostname=HOSTNAME
          --user=USER
          --group=GROUP
          --daemonize
          --pidfile=PIDFILE

      dkfilter.in --help
        to see a full description of the various options

start-stop-daemon: option requires an argument -- x
Try `start-stop-daemon --help' for more information.
failed.
```

So I guess I just need to figure out how to use the script now...

Thanks for all your help!!

---

### Post by steve.horsley on 2007-02-17
Can't help you with your script, I'm afraid. But FYI, unlike windows, the current directory is not normally part of your path, so launching programs in the current directory normally involves tyoing **./program-name**.

---

