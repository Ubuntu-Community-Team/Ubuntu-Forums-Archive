---
title: "After gutsy upgrade my bootmisc.sh doesn't work anymore!"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by mattorama on 2007-10-20
I had bootmisc.sh running a python script. This worked fine in feisty.
After upgrade to gutsy, it doesn't work anymore.

If I run it manually, it runs fine.

Here is my /etc/init.d/bootmisc.sh:

```

#!/bin/sh
### BEGIN INIT INFO
# Provides:          bootmisc
# Required-Start:    $local_fs hostname $remote_fs
# Required-Stop:     $local_fs
# Default-Start:     S
# Default-Stop:
# Short-Description: Miscellaneous things to be done during bootup.
# Description:
### END INIT INFO

PATH=/usr/sbin:/usr/bin:/sbin:/bin
[ "$DELAYLOGIN" ] || DELAYLOGIN=yes
. /lib/init/vars.sh

do_start () {
	#
	# If login delaying is enabled then create the flag file
	# which prevents logins before startup is complete
	#
	case "$DELAYLOGIN" in
	  Y*|y*)
		echo "System bootup in progress - please wait" > /var/lib/initscripts/nologin
		;;
	esac

	# Create /var/run/utmp so we can login.
	: > /var/run/utmp
	if grep -q ^utmp: /etc/group
	then
		chmod 664 /var/run/utmp
		chgrp utmp /var/run/utmp
	fi

	# Set pseudo-terminal access permissions.
	if [ ! -e /dev/.devfsd ] && [ -c /dev/ttyp0 ]
	then
		chmod -f 666 /dev/tty[p-za-e][0-9a-f]
		chown -f root:tty /dev/tty[p-za-e][0-9a-f]
	fi

	# Update motd
	uname -snrvm > /var/run/motd
	[ -f /etc/motd.tail ] && cat /etc/motd.tail >> /var/run/motd

	# Save kernel messages in /var/log/dmesg
	if which dmesg >/dev/null 2>&1
	then
		savelog -q -p -c 5 /var/log/dmesg
		dmesg -s 524288 > /var/log/dmesg
		chgrp adm /var/log/dmesg || :
	elif [ -c /dev/klog ]
	then
		savelog -q -p -c 5 /var/log/dmesg
		dd if=/dev/klog of=/var/log/dmesg &
		sleep 1
		kill $!
		[ -f /var/log/dmesg ] && { chgrp adm /var/log/dmesg || : ; }
	fi

	# Remove bootclean's flag files.
	# Don't run bootclean again after this!
	rm -f /tmp/.clean

	# Start pyTivo  
	echo -n "Starting pyTivo: "  >&2
	/usr/bin/python2.5 /etc/pyTivo/pyTivo.py > /dev/null 2>&1 &
}

case "$1" in
  start|"")
	do_start
	;;
  restart|reload|force-reload)
	echo "Error: argument '$1' not supported" >&2
	exit 3
	;;
  stop)
	# No-op
	;;
  *)
	echo "Usage: bootmisc.sh [start|stop]" >&2
	exit 3
	;;
esac

:

```

Any help is appreciated!

---

### Post by Dr Small on 2007-10-20
How did you normally have it running ?

---

### Post by mattorama on 2007-10-20
It was being run at system startup from the bootmisc.sh script.

---

### Post by mattorama on 2007-10-21
Surely someone can explain what changed between feisty and gutsy.
Did the way init.d scripts get called change?

---

