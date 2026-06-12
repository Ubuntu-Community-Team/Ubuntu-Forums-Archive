---
title: "help with kqemu + qemu"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by supersonicdarky on 2007-04-30
i followed the guide here: [http://ubuntuforums.org/showthread.php?p=200873](http://ubuntuforums.org/showthread.php?p=200873)

i am stumped at this step tho:
> $ sudo gedit /etc/init.d/bootmisc.sh

Add these lines to the end just before "exit;"

# Start Qemu with KQemu accelerator
/sbin/modprobe kqemu
mknod /dev/kqemu c 250 0 # Create the KQEMU device
chmod 666 /dev/kqemu # Make it accessible to all users
where do i add it?

bootmisc.sh:
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

	#
	#	Save udev log in /var/log/udev
	#
	if [ -e /dev/.udev.log ]
	then
		mv -f /dev/.udev.log /var/log/udev
	fi


	# Remove bootclean's flag files.
	# Don't run bootclean again after this!
	rm -f /tmp/.clean
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

help?

---

### Post by joft on 2007-04-30
IMO these lines should go into the "do_start ()" function - right after "rm -f /tmp/.clean" and in front of the following "}". Alternativly, you could add them to the "start" case of the switch statement (after "do_start" and before ";;").

---

