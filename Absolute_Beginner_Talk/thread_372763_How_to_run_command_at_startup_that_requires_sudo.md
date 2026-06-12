---
title: "How to run command at startup that requires sudo"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by meuge on 2007-02-28
Hi

I wanted to mount (read-only) an NTFS partition, and run a command to change my mouse resolution at startup, but both of these commands require priviledges.

Can I write a script of some sort to be able to run these commands at startup?

Thanks in advance!

---

### Post by mr_mop on 2007-02-28
Try adding the NTFS to your /etc/fstab?

It gets mounted at start up then.

---

### Post by bodhi.zazen on 2007-02-28
Add the commands to /etc/init.d/rc.local

You do not need to use sudo as rc.local is run at boot as root ;)

Add the commands above the "exit 0" line.

Use the FULL PATH for your command

---

### Post by nbv4 on 2007-07-27
> **bodhi.zazen said:**
> Add the commands to /etc/init.d/rc.local

You do not need to use sudo as rc.local is run at boot as root ;)

Add the commands above the "exit 0" line.

Use the FULL PATH for your command

I don't see any "exit 0" lines in my /etc/init.d/rc.local file... I see two "exit 3" lines though.


```

#! /bin/sh

PATH=/sbin:/bin:/usr/sbin:/usr/bin
[ -f /etc/default/rcS ] && . /etc/default/rcS
. /lib/lsb/init-functions

do_start() {
	if [ -x /etc/rc.local ]; then
		log_begin_msg "Running local boot scripts (/etc/rc.local)"
		/etc/rc.local
		log_end_msg $?
	fi
}

case "$1" in
    start)
	do_start
        ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac

```

---

### Post by Rocket2DMn on 2007-07-27
It is returning a value to the shell script execution program (the bourne shell to be exact).  the 0, 1, 2, 3, etc following the exit call are just letting the shell know a little something about the reason for exiting.  Some values have particular reserved meanings, others do not.  This is primarily used to debug.

---

### Post by nbv4 on 2007-07-27
> **Rocket2DMn said:**
> It is returning a value to the shell script execution program (the bourne shell to be exact).  the 0, 1, 2, 3, etc following the exit call are just letting the shell know a little something about the reason for exiting.  Some values have particular reserved meanings, others do not.  This is primarily used to debug.

ok, now which one do I put the command above?

---

### Post by bodhi.zazen on 2007-07-27
At the very bottom :

```
#! /bin/sh

PATH=/sbin:/bin:/usr/sbin:/usr/bin
[ -f /etc/default/rcS ] && . /etc/default/rcS
. /lib/lsb/init-functions

do_start() {
	if [ -x /etc/rc.local ]; then
		log_begin_msg "Running local boot scripts (/etc/rc.local)"
		/etc/rc.local
		log_end_msg $?
	fi
}

case "$1" in
    start)
	do_start
        ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac

[b][color=red]# Put your command here, use comments to make note to self
# Added by <user> to ....
command[/color][/b]

# You can add exit 0 if you like, but it is not needed, it just looks cleaner :twisted:
exit 0
```

---

