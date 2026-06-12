---
title: "Mount network drive from wireless laptop"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by burnttoast11 on 2007-09-26
Hello,
I have Ubuntu 7.04 on my laptop and Windows XP on my desktop.
I am trying to mount a shared folder from my desktop on my laptop at boot up.  This wouldn't be a problem if my laptop had a wired connection, but I am using a wireless connection, so I am not connected to my internet connection during boot up.

So does anyone know a work around for this?  Is that a way to run a script automatically after I connect to my wireless network?

Thanks in advance!

Peder L

---

### Post by gareththered on 2007-09-26
As you implied, the problem with network-manager is that it only sets up interfaces after you've logged in.  If this laptop and desktop are relatively static, why don't you set up your interface manually in the file '/etc/network/interfaces' and use the 'post-up' option to mount your share?
You can put any reasonable command in this line e.g.```
post-up mount /media/WinXP
``` if you've previously set up the mount in /etc/fstab'.
I use 'pre-up' not 'post-up' in mine, so I can't say I've tested this!!
There is a man page for the 'interfaces' file and praying to the god of google will no doubt yield some useful information.
Good luck.

---

### Post by burnttoast11 on 2007-09-26
Thanks for the reply!
I tried messing with the "post-up" option in the '/etc/network/interfaces' but I didn't get it to work. Here is what my fstab looked like:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=dd52fd01-2782-46ac-bf25-901c3f885080 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=aa65e392-e3a7-4a51-bce2-2ee7cbf3ac80 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
//192.168.1.8/F /home/peder/shared  smbfs                         0         0

```

My desktop is at 192.168.1.8 and I am sharing a Windows XP folder.  If I type 
```
sudo mount //192.168.1.8/F 
```
into the terminal I can access my folder.  Am I doing something wrong in the fstab?

Here is what I had for my interfaces file.
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp
    post-up mount //192.168.1.8/F /home/peder/shared

auto wlan0
iface wlan0 inet dhcp
```

Is that the proper way to use the post-up option?

---

### Post by gareththered on 2007-09-27
Looking through the boot order, the mounting of your drives takes place _before_ your network is brought  up.  Therefore this idea will not work!  Oops!
]If you type ```
mount -a
``` instead of the specific mount you entered, does the share get mounted?  If so, consider entering a line in '/etc/init.d/rc.local'.

---

### Post by burnttoast11 on 2007-09-27
When I typed
```
mount -a
```
my shared folder got mounted, so my fstab must be correct.  I am pretty new to Ubuntu, so I am not sure what I line I should add to my '/etc/init.d/rc.local'.  What does this file do?
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
Am I supposed to add my mount line somewhere in this?

---

### Post by gareththered on 2007-09-28
If you look in '/etc/rc2.d' you will see many links to files in '/etc/init.d'.  These are all in alphanumeric order starting with the letter 'S'. All these are run in alphanumeric order when the machine boots up (ones beginning with 'K' are run when the machine runs down).  Notice that the link to '/etc/init.d/rc.local' starts with 'S99' therefore is run last.  That file runs the file '/etc/rc.local' therefore anything you enter in this file will be run last.

If you change the file '/etc/rc.local' to```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# Mount SMB share
mount /home/peder/shared
exit 0

```then hopefully it will work for you.

---

### Post by burnttoast11 on 2007-09-28
I tried changing my '/etc/init.d/rc.local' file to what you suggested, but I think that that script is still running before I connect to the internet.  Even after I am booted, I have to type in the password for my 'default keyring' and then I connect to the internet.  

 When you say I should change my execution bits would the following be correct:
```
chmod +x rc.local
```
Since the mount wasn't up automatically, I tried running rc.local to see if it was working
```
./rc.local
```
The script mounted my network drive when I ran it manually.

So, thanks for all of the suggestions.  If you have anymore I would love to here them, but otherwise it's really not too much of a problem to manually mount the network drive each time I start my computer.

---

### Post by gareththered on 2007-09-28
Doh!  I forgot about the wireless applet.  I fire up my wireless connection at boot time using '/etc/network/interfaces' as I use my machine as an internet gateway.
But, I do think that the scripts within the '/etc/network/if-up.d' directory are run when a network comes online even when instigated by nm-applet.  It may be worth investigating these.  Good Luck!

---

