---
title: "how do you dump logs / kernel log / syslog to bash terminal in a user friendly way?"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by z4pp4 on 2006-04-12
Hi there
I want to watch all logging activities that goes on in my system from my bash / *sh terminal and would like to have some user friendlyness thrown in to boot :)

What I would like to happen is:
```
you@yourPC~$ ls whatever
[COLOR="RoyalBlue"]access log: A user has logged on[/COLOR]
[COLOR="Lime"]apache log: somebody has visited your homepage[/COLOR]
...
[COLOR="Navy"]
whatever1   whatever2    whatever3[/COLOR]

you@yourPC~$ _
```

The trick is that the logs cannot interrupt the bash session while you are typing (this messes things up), and the logs have to dump right after you type enter, but before the command you requested executes. Thus, something like dmesg & will not work.

Any ideas guys?

---

### Post by nanotube on 2006-04-12
why not just open a second terminal to keep the logs in? :)

---

### Post by Mustard on 2006-04-12
I'm not sure how you would get what you are after above, but I wonder whether an app like root-portal is something that you would like.

It's avaialable in the repositories I believe or can be installed from source.
[http://freshmeat.net/projects/root-portal/](http://freshmeat.net/projects/root-portal/)

---

### Post by z4pp4 on 2006-04-12
Hi... thanks for the responses so far.
As to the reason behind this: I do a lot of network specific stuff, and would like to know for example what effect my commands / jobs / etc. has on the network, and to monitor things as they happen, for example port scans.
I think that dumping logs (ok not all of them - maybe only error / warnings) will make the shell more interactive and give you greater insight into what is going on in your machine...like knowing when a cron job starts so that you can blame your slow machine on something.
Root portal looks nice, and I will certainly use it, thanks. Although, its a bit too "graphical" if you know what I mean. Sometimes I like plain shells, especially when doing remote access, since they teach you more than the GUI.
What I had in mind is some sort of alias "script" or something that you put in your .bashrc?

---

### Post by engla on 2006-04-12
Use the bash env PROMPT_COMMAND.

I experimented, and this works to write out the last line of messages after each prompt:
```
export PROMPT_COMMAND='tail -n 1 /var/log/messages.0'
```

But that's only the proof of concept. Make prompt_command run a script you wrote. 
The script would: 
[LIST]
[*]If some files have changed since the last timestamp, write out the end of some files*****
[*]Set a new timestamp
[/LIST]
*** Addition**: you could actually store away a copy of the files you monitor and diff them to find out which lines where added, if all files are just log files that are appended to. [careful with log rotation though]

---

### Post by z4pp4 on 2006-04-12
I have looked around and it seems that 
```
tail -f & 
```

is about halfway there. 
Now, the only things I need to see is how to use 
```
echo -en "\\e[some colourm  `tail -f &` ..........
```

to display the logs in color
Also, I need to see how to block background processes from producing output while the foreground shell is waiting for a command.

How is this blocking done?

---

### Post by engla on 2006-04-14
I thought this was interesting, so I tried to make something for this according to my idea above.

It's a bash script, included above. Save it to a file like monitor_log.sh. You use it like "sh monitor_log.sh /var/log/messages.0". The first run it basically outputs nothing, but it should in subsequent runs output the lines added to the logfile (if any).

So you can use it like you wished if you do
export PROMPT_COMMAND="sh ~/monitor_log.sh /var/log/messages.0"
in your .bashrc file.

This is just a more concrete example of what I said above. It's too slow, to ugly etc, but try it and hack away.

```
#!/bin/bash


# Constants
WD="/tmp"
# Variables
LOGFILE="$1"
CHKSUM=`echo "$LOGFILE" | md5sum | cut -b 0-32`
STAMPFILE="$WD/monitor_log_$CHKSUM"

# Exit if any command does not exit with 0 (succ)
set -e

if [ -z "$1" -o ! -e "$1" ] ; then
	echo "No such file: '$1'" 
	echo Usage: $0 logfile
	exit 1
fi

U=`id -u`
if [ "$U" -eq "0" ] ; then
	echo "Don't run this script as root,"
	echo "it is probably dangerous"
	exit 1
fi


if [ -e "$STAMPFILE" ]; then
	TMP=`tempfile`

	set +e

	diff -u0 "$STAMPFILE" "$LOGFILE" | grep -vE "^((\+\+\+)|(-)|(@@))" > "$TMP"

	set -e

	cat "$TMP"

else
	echo "No stampfile at $STAMPFILE"
fi

cp "$LOGFILE" "$STAMPFILE"
```

---

### Post by z4pp4 on 2006-04-18
Working..

---

### Post by z4pp4 on 2006-04-18
Hi. Thanks for the response.
I've narrowed down the scripts to the following:

Insert this in the users' .bashrc:
```

export PROMPT_COMMAND='if [ "0" -ne `du /tmp/logcache | cut -b "1-1"` ]; then echo -e "\E[00;34m\033[1m`cat /tmp/logcache`\033[0m"; cat /dev/null > /tmp/logcache; fi'
cat /dev/null > /tmp/logcache

```

Insert this in a script called /etc/init.d/logcache:
```

#!/bin/sh  

# rc.logcache 0.01 2006/02/13 (z4pp4)
# This is designed to work in BSD as well as SysV init setups.  See
# the HOWTO for customization instructions.
# Tags for Red Hat init configuration tools
#
# chkconfig: 2345 45 96
# processname: logcache
# description: This script enables caching of system and other logs for live display on the terminal. Change commands where required by editing the script. Comments? info [ the at here] ilumen.co.za

usage()
{
    echo "This script enables caching of system and other logs for live display on the terminal. Change commands where required by editing the script. Comments? info [ the at here] ilumen.co.za"
    echo "Usage: $0 {start|stop|status|restart|reload|force-reload}"
}

    if [ $# -lt 1 ] ; then usage ; fi
    action=$1

    case "$action" in

    start)
	echo "Starting logcache..."
# TODO START MARKER: Edit these logs to your liking.
tail -n1 -f /var/log/dmesg >>/tmp/logcache &
tail -n1 -f /var/log/messages >>/tmp/logcache &
tail -n1 -f /var/log/auth.log >>/tmp/logcache &
tail -n1 -f /var/log/daemon.log >>/tmp/logcache &
tail -n1 -f /var/log/dmesg >>/tmp/logcache &
tail -n1 -f /var/log/kernel >>/tmp/logcache &
tail -n1 -f /var/log/loginlog >>/tmp/logcache &
tail -n1 -f /var/log/tor/log >>/tmp/logcache &
tail -n1 -f /var/log/Xorg.0.log >>/tmp/logcache &
# TODO END MARKER

tcpdump >>/tmp/logcache &
cat /dev/null > /tmp/logcache

	;;

    stop)
	echo "Stopping logcache..."
killall tail        
	;;

    status)
	echo "No status currently."
	;;

    restart)
	$0 stop
	$0 start
	;;

    reload|force-reload)
	$0 restart
	;;

    *)
	usage
	;;

    esac

```

Insert this as a script called /etc/cron.daily/logcache:
```

#!/bin/sh
cat /dev/null > /tmp/logcache

```

To make the scripts execute properly, do
```

sudo chmod +x /etc/cron.daily/logcache
sudo chmod +x /etc/init.d/logcache
sudo chmod +w /tmp/logcache
update-rc.d logcache defaults

```

This should work quite nicely...

---

