---
title: "[SOLVED] modify checkfs to support fsck.hfsplus"
date: 2008-05-06
forum: Apple Hardware Users
---

### Post by flaggh on 2008-05-06
I noticed that checkfs does not successfully run fsck.hfsplus because it tries to use the unsupported -a option.  Here's the contents of the log file /var/log/fsck/checkfs

```
Log of fsck -C3 -R -A -a 
Tue May  6 15:25:36 2008

fsck 1.40.8 (13-Mar-2008)
fsck.hfsplus: invalid option -- a
usage: fsck.hfsplus [-dfl m [mode] npqruy] special-device
  d = output debugging info
  f = force fsck even if clean (preen only) 
  l = live fsck (lock down and test-only)
  m arg = octal mode used when creating lost+found directory 
  n = assume a no response 
  p = just fix normal inconsistencies 
  q = quick check returns clean, dirty, or failure 
  r = rebuild catalog btree 
  u = usage 
  y = assume a yes response 
fsck died with exit status 1

Tue May  6 15:25:37 2008
----------------
```

I've taken a look at the /etc/init.d/checkfs.sh script and wanted to modify it.  I thought the appropriate change would be to insert an if statement around line 55 that passes the -p argument if $FSCKTYPES = hfsplus.  Has anybody tried this before?  Do you think I'm going about it the wrong way?

---

### Post by flaggh on 2008-05-07
Can anybody verify the modification I have made will work before I go ahead and test the script on my system?  I've highlighted the change in red:
```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          checkfs
# Required-Start:    modutils checkroot
# Required-Stop:
# Should-Start:      lvm cryptdisks
# Should-Stop:
# Default-Start:     S
# Default-Stop:
# Short-Description: Check all filesystems.
### END INIT INFO

PATH=/sbin:/bin
FSCK_LOGFILE=/var/log/fsck/checkfs
[ "$FSCKFIX" ] || FSCKFIX=no
. /lib/init/vars.sh

. /lib/lsb/init-functions

# Always output fsck progress
stdin=`readlink /proc/self/fd/0`
if [ "${stdin#/dev/null}" != "$stdin" ]; then
    exec </dev/console >/dev/console 2>&1
fi

do_start () {
	# See if we're on AC Power
	# If not, we're not gonna run our check
	if which on_ac_power >/dev/null 2>&1
	then
		on_ac_power >/dev/null 2>&1
		if [ $? -eq 1 ]
		then
			[ "$VERBOSE" = no ] || log_success_msg "Running on battery power, so skipping file system check."
			BAT=yes
		fi
	fi

	#
	# Check the rest of the file systems.
	#
	if [ ! -f /fastboot ] && [ ! "$BAT" ] && [ "$FSCKTYPES" != "none" ]
	then
		if [ -f /forcefsck ]
		then
			force="-f"
		else
			force=""
		fi
		if [ "$FSCKFIX" = yes ]
		then
			fix="-y"
		else
[COLOR="Red"]			if [ "$FSCKTYPES" = "hfsplus" ]
				fix="-p"
			else
				fix="-a"
			fi[/COLOR]
		fi
		spinner="-C"
		case "$TERM" in
		  dumb|network|unknown|"")
			spinner=""
			;;
		esac
		[ "$(uname -m)" = s390 ] && spinner=""  # This should go away
		FSCKTYPES_OPT=""
		[ "$FSCKTYPES" ] && FSCKTYPES_OPT="-t $FSCKTYPES"
		handle_failed_fsck() {
			log_failure_msg "File system check failed. 
A log is being saved in ${FSCK_LOGFILE} if that location is writable. 
Please repair the file system manually."
			log_warning_msg "A maintenance shell will now be started. 
CONTROL-D will terminate this shell and resume system boot."
			# Start a single user shell on the console
			if ! sulogin $CONSOLE
			then
				log_failure_msg "Attempt to start maintenance shell failed. 
Continuing with system boot in 5 seconds."
				sleep 5
			fi
		}
		if [ "$VERBOSE" = no ]
		then
			log_action_begin_msg "Checking file systems"
			logsave -s $FSCK_LOGFILE fsck $spinner -R -A $fix $force $FSCKTYPES_OPT
			FSCKCODE=$?
			if [ "$FSCKCODE" -gt 1 ]
			then
				log_action_end_msg 1 "code $FSCKCODE"
				handle_failed_fsck
			else
				log_action_end_msg 0
			fi
		else
			if [ "$FSCKTYPES" ]
			then
				log_action_msg "Will now check all file systems of types $FSCKTYPES"
			else
				log_action_msg "Will now check all file systems"
			fi
			logsave -s $FSCK_LOGFILE fsck $spinner -V -R -A $fix $force $FSCKTYPES_OPT
			FSCKCODE=$?
			if [ "$FSCKCODE" -gt 1 ]
			then
				handle_failed_fsck
			else
				log_success_msg "Done checking file systems. 
A log is being saved in ${FSCK_LOGFILE} if that location is writable."
			fi
		fi
	fi
	rm -f /fastboot /forcefsck
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
	echo "Usage: checkfs.sh [start|stop]" >&2
	exit 3
	;;
esac

:
```

Thanks in advance for any help and suggestions.  I would greatly appreciate any input.

---

### Post by cyberdork33 on 2008-05-07
EDIT: nvm. misread the problem to begin with.

---

### Post by flaggh on 2008-05-17
Just in case anybody is wondering how I solved this problem, rather than modify the checkfs script, I decided to recompile fsck.hfsplus to accept the -a option for backwards compatibility.  I modified the source code to map the -a option to be equivalent to the -p option, which was a relatively straigh forward fix.  This seems to be working fine for now.  I'll let everyone know if I run into any problems.

---

