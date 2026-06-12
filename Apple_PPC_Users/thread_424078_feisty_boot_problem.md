---
title: "feisty boot problem"
date: 2007-04-26
forum: Apple PPC Users
---

### Post by mrqwa on 2007-04-26
hi,
i have a problem.
i´ve upgraded on feisty fawn yesterday, and now a i can´t star my computer
when i turn on my mac, everythin seems ok, xubuntu progress bar fills up, but after that it changes to normal black and white screen with this text

```
udevd-event[1787]: run_program: open /dev/null failed: no such file or directory
init:/etc/event.d/control-alt-delete:6: Unknown stanza
init:/etc/event.d/logd2:13: Unknown stanza
init:/etc/event.d/sulogin:6: Unknown stanza
init:/etc/event.d/tty1:13: Unknown stanza
init:/etc/event.d/tty2:13: Unknown stanza
init:/etc/event.d/tty3:13: Unknown stanza
init:/etc/event.d/tty4:13: Unknown stanza
init:/etc/event.d/tty5:13: Unknown stanza
init:/etc/event.d/tty6:13: Unknown stanza
devd[1929]: add_to_rules: PHYSDEV* values are deprecated and will be removed from a future kernel, please fix it in /etc/udev/ruled.d/40-permissions.rules:17
devd[1929]: add_to_rules: PHYSDEV* values are deprecated and will be removed from a future kernel, please fix it in /etc/udev/ruled.d/40-permissions.rules:45
udevd[1929]: lookup_group: specified group 'nvram' unknown
udevd[1929]: udev_rules_init: could not read '/etc/udev/rules.d/60-libpisock.rules': No such file or directory
udevd[1929]: add_to_rules: do not reference parent sysfs directories directly, that may break with future kernel, please fix it in /etc/udev/rules.d/65-persistent-storage.rules:12
* Activating swap
* Checking root file system…
fsck 1.40-WIP (14-Nov-2006)
/dev/hda3: clean, 218730/4931584 files, 9239843/9849609 blocks

* Checking file systems…
fsck 1.40-WIP (14-Nov-2006)
```

picture is here [[IMG]http://img49.imageshack.us/img49/1476/ubuntu002ag0.th.jpg[/IMG]](http://img49.imageshack.us/my.php?image=ubuntu002ag0.jpg)

and it doesn´t continue.... please help!
thanks

mrqwa
p.s.: sorry for my not very good english

---

### Post by dpny on 2007-04-26
I was getting the same error. Haven't been able to boot Feisty at all.

---

### Post by mrqwa on 2007-04-26
and how did you solved it?
it is possible to recover old system from live cd? or what? thanks a lot

---

### Post by dpny on 2007-04-26
> **mrqwa said:**
> and how did you solved it?
it is possible to recover old system from live cd? or what? thanks a lot

I haven't been able to solve it. I haven't been able to boot Feisty at all.

---

### Post by ubuntubrian on 2007-04-26
This is not much help but I found that I couldn't boot the Feisty stable live cd at all. I got the ubuntu start up graphics and then a blank screen with an Ubuntu color. I was able to boot the last beta version of Feisty live cd so something changed on the route to stable. The Beta was an official release and the stable is unofficial so maybe something there. I'd try to get an earlier version live cd and boot from that. Mayber even use Dapper or Edgy as there have been quite a few problems with Feisty stable on ppc.
Good luck.

---

### Post by rdejean on 2007-04-27
The problem is with the 'Unknown stanza' error messages in event.d.  A typo prevents the getty's from starting on the virtual terminals.  So you never get a login prompt.

Look at /etc/event.d/tty1.  The 2 last lines should look like this:

exec /sbin/getty 38400 tty1
respawn


Notice the very very bad typos... i'm not sure how such a bug slipped through.  Fix it in the tty1 through tty6 files, reboot, and you should be able to login.   Perhaps someone can report this bug if it's not already known.  I haven't looked yet.

I just upgraded from dapper to edgy to feist.  Now on to the next problem haha.

ray

---

### Post by Aperium on 2007-04-27
> **rdejean said:**
> The problem is with the 'Unknown stanza' error messages in event.d.  A typo prevents the getty's from starting on the virtual terminals.  So you never get a login prompt.

Look at /etc/event.d/tty1.  The 2 last lines should look like this:

exec /sbin/getty 38400 tty1
respawn

Notice the very very bad typos... i'm not sure how such a bug slipped through.  Fix it in the tty1 through tty6 files, reboot, and you should be able to login.

ray
And how would you suggest we go about fixing it?

---

### Post by James Keating on 2007-04-30
rdejean's fix worked for me.

The boot process would hang after the last script in /etc/rc2.d, no matter which script that was. (I have put the nosplash option in /boot/grub/boot/menu.lst, so I can see the boot messages.)
Earlier in the boot process, I would get the messages
init:/etc/event.d/tty1:13: Unknown stanza
init:/etc/event.d/tty2:13: Unknown stanza

The problem was in /etc/event.d/tty1 (and tty2 etc.)
The last two lines were
respawn
/sbin/getty 38400 tty1exec /sbin/getty 38400 tty1

but should have been
exec /sbin/getty 38400 tty1
respawn

After fixing each of the tty files, the machine booted fine, though it needs a little push at the end by pressing enter.

This seems to be a known bug. The release notes ([http://www.ubuntu.com/getubuntu/releasenotes/704](http://www.ubuntu.com/getubuntu/releasenotes/704)) say:
Users who have serial consoles, or have made custom changes to the /etc/inittab file or files in the /etc/event.d directory should be aware that the format of these files have changed slightly and your changes will not be automatically migrated. Bug #89314. The following changes should be made.
"respawn COMMAND" should be changed to "exec COMMAND" with "respawn" on a seperate line.
"on EVENT" should be changed to "start on EVENT"
the "runlevel-X" events should be changed to "runlevel X"

I only changed inittab to comment out all but the first two tty processes (# 3:23:respawn:/sbin/getty 38400 tty3) to not waste the memory. I didn't make the kind of change Ubuntu warned about, but it seems to have been enough.

---

### Post by braime on 2007-04-30
hi,

after the kernel-update, i am "pleased" with the same problem/bug.

> **James Keating said:**
> rdejean's fix worked for me.

The boot process would hang after the last script in /etc/rc2.d, no matter which script that was. (I have put the nosplash option in /boot/grub/boot/menu.lst, so I can see the boot messages.)
Earlier in the boot process, I would get the messages
init:/etc/event.d/tty1:13: Unknown stanza
init:/etc/event.d/tty2:13: Unknown stanza

The problem was in /etc/event.d/tty1 (and tty2 etc.)
The last two lines were
respawn
/sbin/getty 38400 tty1exec /sbin/getty 38400 tty1

but should have been
exec /sbin/getty 38400 tty1
respawn

After fixing each of the tty files, the machine booted fine, though it needs a little push at the end by pressing enter.



worked quite well, i could eleminate these errors:

init:/etc/event.d/tty1:13: Unknown stanza
init:/etc/event.d/tty2:13: Unknown stanza
init:/etc/event.d/tty3:13: Unknown stanza
init:/etc/event.d/tty4:13: Unknown stanza
init:/etc/event.d/tty5:13: Unknown stanza
init:/etc/event.d/tty6:13: Unknown stanza


now those are left:

init:/etc/event.d/control-alt-delete:6: Unknown stanza
init:/etc/event.d/logd2:13: Unknown stanza
init:/etc/event.d/sulogin:6: Unknown stanza

the three lines are still bothering me, and no matter what i change in these files, i was not able to boot, up to now. if someone could help me, he would rise to my personal hero for at least some time ;-)

Another question to this smart guy would be, why every file is double, for example:
tty1  and  tty1.dpkg-new, (but this is less important and more explainable) ?


Greeetz and Thx
Daniel

---

### Post by braime on 2007-05-02
:(  why does no one reply?
was is an error in netiquette?
shall i post some infos or files?
is it my horrible denglish?


please help me with busting these errors to finally be able to boot feisty:

init:/etc/event.d/control-alt-delete:6: Unknown stanza
init:/etc/event.d/logd2:13: Unknown stanza
init:/etc/event.d/sulogin:6: Unknown stanza


*very worried
Daniel

---

### Post by Aperium on 2007-05-02
> **braime said:**
> :(  why does no one reply?
was is an error in netiquette?
shall i post some infos or files?
is it my horrible denglish?


please help me with busting these errors to finally be able to boot feisty:

init:/etc/event.d/control-alt-delete:6: Unknown stanza
init:/etc/event.d/logd2:13: Unknown stanza
init:/etc/event.d/sulogin:6: Unknown stanza


*very worried
Daniel
There is no reason to be worried, except for your computer.  Perhaps the reason that no one has responed is that no one has a solution, or perhaps someone who could help doen't have enough information to help.

Personally, I had the same problem you did, with the exception that I lack the knoledge of how to make the necessary changes to the tty files, so I still have all nine errors.

Posting the contents of the three files that are throwing the errors may help someone figure out what is wrong.

I wish I could help more,
Daniel

---

### Post by Aperium on 2007-05-02
**[COLOR="Red"]I do not know what I'm doing. This fix is purely expirimental.[/COLOR]**

In the file */etc/event.d/control-alt-delete* line six reads:
```
on ctrlaltdel
```
you need to add the word 'start' in front of this.
It should look like this:
```
start on ctrlaltdel
```

I'm looking in to the other errors...

---

### Post by Aperium on 2007-05-02
**[COLOR="Red"]These fixes are purely expirimental.[/COLOR]**

line 11 of file [FONT="Fixedsys"]logd[/FONT] looks like this:
```
respawn //sbin/logd
```
but should be changed to:
```
exec //sbin/logd
respawn
```

I don't have a [FONT="Fixedsys"]logd2[/FONT] file, but line 13 of [FONT="Fixedsys"]logd2[/FONT] may look simmilar to line 6 of [FONT="Fixedsys"]logd[/FONT]



line 6 of [FONT="Fixedsys"]sulogin[/FONT] looks like:
```
on stalled
```
but should be:
```
start on stalled
```
there may still be a problem with line 11 of [FONT="Fixedsys"]sulogin[/FONT].

Line 11 reads:
[CODE]start script[\CODE]
I got a "duplicate value" message when I removed the word 'start' from the line.
changing it to the following will stop the error but may not be the correct solution.
[CODE]pre-start script[\CODE]


[B]The result of these changes is a black screen with a blinking cursor.
 Pressing Enter will bring you to a black screen without a cursor.
 Ubuntu does NOT boot.[/B]

Anyone know what to do now?

---

### Post by James Keating on 2007-05-03
I can't tell you what's wrong, since I haven't had a similar problem and have never touched those files. But since you ask and are waiting, here are the contents of my files, which work for me. 

-----------------------------------------
/etc/event.d/control-alt-delete:

# control-alt-delete - emergency keypress handling
#
# This task is run whenever the Control-Alt-Delete key combination is
# pressed.  Usually used to shut down the machine.

start on control-alt-delete

exec /sbin/shutdown -r now "Control-Alt-Delete pressed"


----------------------------
/etc/event.d/sulogin:

# sulogin - rescue mode
#
# This task ensures that should the system fail to have any active jobs
# that the system administrator can rescue it; by giving them a shell.

# Disabled since this would get started when init is re-exec'd, and
# "console owner" kills X.
# start on stalled

exec /sbin/sulogin
console owner

pre-start script
	echo
	echo "The system has reached a state where there are no jobs running."
	echo "A shell will be spawned so that you may start such jobs that are"
	echo "necessary."
	echo
	echo "Type 'exit' when finished."
end script


-----------------------
/etc/event.d/logd:

# logd
#
# This service is started automatically by init so that the output from
# other services can be logged.

description	"service logging daemon"
author		"Scott James Remnant <scott@ubuntu.com>"

stop on runlevel 0
stop on runlevel 1
stop on runlevel 6

console output

exec /sbin/logd
respawn

---

### Post by braime on 2007-05-03
Hi,

first of all, thank you very much for the help so far!!!

Update:
With the correct files i could eleminate the three errors. That makes James my personal hero, but still i can not boot, because i did not read till the end. Or in other words: the obvious errors made me overlook the other(s) or was it the other way aroud:

udev_rules_init: could not read '/etc/udev/rules.d/60-libpisock.rules': No such file or directory

this is (hopefully) the last obstacle before booting. the strange thing is:
- the file exists!
-  i use ext-volume-manager under a not-unix-os ;-) if i right-klick on the file (60-libpisock.rules) my systems reboots with a hard error. I am not allowed to move the whole directory.

Could someone (James ;-)) could please post his "healthy" 60-libpisock.rules-file or an idea, how i could bust this last problem?


Greetz
Daniel

---

### Post by Aperium on 2007-05-03
Thanks for the contents of those files James. I'll try using them on my Ubuntu when I next have access to it(probably tomorrow afternoon).

I had a simmilar problem to Daniel's current one, except that it was '/etc/udev/libpisock9.rules' that could not be found.  The file did not exist, so I copied it from the Feisty CD I am using.  Unfourtunatly my computer still does not boot, but again that may be due to errors in the three '/etc/event.d/' files.

---

### Post by braime on 2007-05-04
hi again,

@ Aperium:
i can not locate the *.rules files on my feisty-cd, are they not created while compiling?
where on my cd could i find them?

Greetz
Daniel

---

### Post by James Keating on 2007-05-04
I don't have a /etc/udev/rules.d/60-libpisock.rules file. However, here are the contents of the file as contained in the package pilot-link_0.12.1-5.deb:

--------------------------------------------------------------------------------------------

# udev rules file for pilot-link's libpisock library, enabled for libusb
#
BUS!="usb", ACTION!="add", GOTO="libpisock_rules_end"

# Sony handheld devices
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="0038", GROUP="dialout", MODE="0664"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="0066", GROUP="dialout", MODE="0664"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="0095", GROUP="dialout", MODE="0664"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="009a", GROUP="dialout", MODE="0664"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="00da", GROUP="dialout", MODE="0664"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="00e9", GROUP="dialout", MODE="0664"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="0144", GROUP="dialout", MODE="0664"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="0169", GROUP="dialout", MODE="0664"

# Handspring handheld devices
SYSFS{idVendor}=="082d", SYSFS{idProduct}=="0100", GROUP="dialout", MODE="0664"
SYSFS{idVendor}=="082d", SYSFS{idProduct}=="0200", GROUP="dialout", MODE="0664"
SYSFS{idVendor}=="082d", SYSFS{idProduct}=="0300", GROUP="dialout", MODE="0664"

# Palm, Inc. and palmOne handheld devices
SYSFS{idVendor}=="04e8", SYSFS{idProduct}=="6601", GROUP="dialout", MODE="0664"
SYSFS{idVendor}=="04e8", SYSFS{idProduct}=="8001", GROUP="dialout", MODE="0664"
SYSFS{idVendor}=="0830", SYSFS{idProduct}=="0001", GROUP="dialout", MODE="0664"
SYSFS{idVendor}=="0830", SYSFS{idProduct}=="0002", GROUP="dialout", MODE="0664"
SYSFS{idVendor}=="0830", SYSFS{idProduct}=="0003", GROUP="dialout", MODE="0664"
SYSFS{idVendor}=="0830", SYSFS{idProduct}=="0020", GROUP="dialout", MODE="0664"
SYSFS{idVendor}=="0830", SYSFS{idProduct}=="0031", GROUP="dialout", MODE="0664"
SYSFS{idVendor}=="0830", SYSFS{idProduct}=="0040", GROUP="dialout", MODE="0664"
SYSFS{idVendor}=="0830", SYSFS{idProduct}=="0050", GROUP="dialout", MODE="0664"
SYSFS{idVendor}=="0830", SYSFS{idProduct}=="0060", GROUP="dialout", MODE="0664"
SYSFS{idVendor}=="0830", SYSFS{idProduct}=="0061", GROUP="dialout", MODE="0664"
SYSFS{idVendor}=="0830", SYSFS{idProduct}=="0070", GROUP="dialout", MODE="0664"
SYSFS{idVendor}=="0830", SYSFS{idProduct}=="0080", GROUP="dialout", MODE="0664"

# Garmin iQue 3600
SYSFS{idVendor}=="091e", SYSFS{idProduct}=="0004", GROUP="dialout", MODE="0664"
SYSFS{idVendor}=="0c88", SYSFS{idProduct}=="0021", GROUP="dialout", MODE="0664"

# Tapwave Zodiac 1 & 2
SYSFS{idVendor}=="12ef", SYSFS{idProduct}=="0100", GROUP="dialout", MODE="0664"

# Unknown device (can someone confirm?)
SYSFS{idVendor}=="4766", SYSFS{idProduct}=="0001", GROUP="dialout", MODE="0664"

LABEL="libpisock_rules_end"

--------------------------------------------------------------------------------------------

If this does not help, try moving the file out of that directory (to, say, your home directory). I imagine you could boot then, and re-install the package. Since this is due to a bug in migrating files that you have altered in /etc/udev, a re-install should write a correct file.

---

### Post by braime on 2007-05-04
Thanks James, i did not succed in replacing the file from windows. ("blabla this file is used by another programm etc...)
will try a live-cd tomorrow and give an update!

---

### Post by braime on 2007-05-07
hi,

now i have my mashine working again, but i did not solve the problem. i formated the partition and installed a fresh copy of feisty.

the "healthy" 60-libpisock eleminated the error-line in the boot-process, but still the system hang at that exact same moment, without any error-messages.

thanks for your help, i think i might need it again ;-)

daniel

p.s.: extra compliment for this very very usefull forum!

---

### Post by Aperium on 2007-05-07
Yes, my problem is the same. After repairing all of the listed errors, I'm left with a black screen when it tries to boot.

I haven't resigned myself to reinstalling Feisty yet, but that time may not be far off.

Thanks for the help both of you.

---

### Post by mrqwa on 2007-05-09
thanks a lot!
last problem, these lines
> 
devd[1929]: add_to_rules: PHYSDEV* values are deprecated and will be removed from a future kernel, please fix it in /etc/udev/ruled.d/40-permissions.rules:17
devd[1929]: add_to_rules: PHYSDEV* values are deprecated and will be removed from a future kernel, please fix it in /etc/udev/ruled.d/40-permissions.rules:45
udevd[1929]: lookup_group: specified group 'nvram' unknown
udevd[1929]: udev_rules_init: could not read '/etc/udev/rules.d/60-libpisock.rules': No such file or directory
udevd[1929]: add_to_rules: do not reference parent sysfs directories directly, that may break with future kernel, please fix it in /etc/udev/rules.d/65-persistent-storage.rules:12

any ideas? thanks!

---

### Post by stmiller on 2007-05-09
When replying, please give your exact mac model. Do you all have a white iMac G4?

---

### Post by James Keating on 2007-05-09
This is now seriously over my head, but here goes:

-----------------------------------------------------
/etc/udev/ruled.d/40-permissions.rules:

Lines 17 and 45 are a problem in your file. My file has no PHYSDEV. Yours does, and the wording has to be changed somehow. The manpage doesn't refer to PHYSDEV. My file reads:

# This file establishes permissions and ownership of devices according
# to Ubuntu policy.  See udev(7) for syntax.
#
# The names of the devices must not be set here, but in 20-names.rules;
# user-friendly symlinks (which need no permissions or ownership) should
# be set in 60-symlinks.rules.

# Block devices
SUBSYSTEM!="block", GOTO="block_end"
ATTRS{removable}!="1",			GROUP="disk"
ATTRS{removable}=="1",			GROUP="floppy"
SUBSYSTEMS=="usb",			GROUP="plugdev"
SUBSYSTEMS=="ieee1394",			GROUP="plugdev"
LABEL="block_end"

# IDE devices
ENV{ID_CDROM}=="?*",			GROUP="cdrom"
KERNEL=="ht[0-9]*",			GROUP="tape"
KERNEL=="nht[0-9]*",			GROUP="tape"

# IEEE1394 (firewire) devices
# Please note that raw1394 gives unrestricted, raw access to every single
# device on the bus and those devices may do anything as root on your system.
# Yes, I know it also happens to be the only way to rewind your video camera,
# but it's not going to be group "video", okay?
KERNEL=="raw1394",			GROUP="disk"
KERNEL=="dv1394*",			GROUP="video"
KERNEL=="video1394*",			GROUP="video"

# Packet CD devices, group under /dev/pktcdvd
KERNEL=="pktcdvd",			MODE="0644"
KERNEL=="pktcdvd[0-9]*",		GROUP="cdrom"

# Printers and Parallel devices
SUBSYSTEM=="printer",			GROUP="lp"
SUBSYSTEM=="ppdev",			GROUP="lp"
SUBSYSTEM=="usb", KERNEL=="lp[0-9]*",	GROUP="lp"
KERNEL=="pt[0-9]*",			GROUP="tape"
KERNEL=="pht[0-9]*",			GROUP="tape"

# SCSI devices
SUBSYSTEMS=="scsi", GOTO="scsi_start"
GOTO="scsi_end"
LABEL="scsi_start"
ATTRS{type}=="1",			GROUP="tape"
ATTRS{type}=="5",			GROUP="cdrom"
ATTRS{type}=="6",			GROUP="scanner"
ATTRS{type}=="3", ATTRS{vendor}=="HP",	GROUP="scanner"
ATTRS{type}=="3", ATTRS{vendor}=="Epson", GROUP="scanner"
LABEL="scsi_end"

# Serial devices
SUBSYSTEM=="tty",			GROUP="dialout"
SUBSYSTEM=="capi",			GROUP="dialout"
SUBSYSTEM=="slamr",			GROUP="dialout"
SUBSYSTEM=="zaptel",			GROUP="dialout"
KERNEL=="ttyLTM[0-9]*",			GROUP="dialout", MODE="0660"

# Sound devices
SUBSYSTEM=="sound",			GROUP="audio"

# USB devices (usbfs replacement)
SUBSYSTEM=="usb_device",		MODE="0664"

# vc (virtual console) devices
SUBSYSTEM!="tty", GOTO="vc_end"
KERNEL=="console",			GROUP="root", MODE="0600"
KERNEL=="ptmx",				GROUP="root", MODE="0666"
KERNEL=="pty*",				GROUP="tty", MODE="0666"
KERNEL=="tty",				GROUP="root", MODE="0666"
KERNEL=="tty[0-9]*",			GROUP="root"
LABEL="vc_end"

# Video devices
SUBSYSTEM=="drm",			GROUP="video"
SUBSYSTEM=="dvb",			GROUP="video"
SUBSYSTEM=="graphics",			GROUP="video"
SUBSYSTEM=="video4linux",		GROUP="video"
KERNEL=="agpgart",			GROUP="video"
KERNEL=="nvidia*",			GROUP="video"

# Other devices, by name
KERNEL=="null",				MODE="0666"
KERNEL=="zero",				MODE="0666"
KERNEL=="full",				MODE="0666"
KERNEL=="random",			MODE="0666"
KERNEL=="urandom",			MODE="0666"
KERNEL=="mem",				GROUP="kmem", MODE="0640"
KERNEL=="kmem",				GROUP="kmem", MODE="0640"
KERNEL=="port",				GROUP="kmem", MODE="0640"
KERNEL=="nvram",			GROUP="kmem"
KERNEL=="rtc",				GROUP="audio"
KERNEL=="inotify",			MODE="0666"
KERNEL=="js[0-9]*",			GROUP="plugdev"


-----------------------------------------------------
udevd[1929]: lookup_group: specified group 'nvram' unknown:

Um, some boot file refers to the group nvram. If you remove (or comment out) that line, it'll be OK. /etc/udev/ruled.d/20-names.rules and /etc/udev/ruled.d/40-permissions.rules have references to groups. You can find the file from the command line with grep nvram  * (or, to search subdirectories as well, rgrep nvram *). If you can get a GUI, try gnome-search-tool or sagasu.

-----------------------------------------------------
/etc/udev/rules.d/65-persistent-storage.rules:

Your line 12 is a problem somehow. For comparison, my file reads:

 # persistent storage links: /dev/{disk,tape}/{by-id,by-uuid,by-label,by-path,by-name}
# scheme based on "Linux persistent device names", 2004, Hannes Reinecke <hare@suse.de>

ACTION=="add|change", GOTO="persistent_storage_start"
GOTO="persistent_storage_end"

LABEL="persistent_storage_start"

KERNEL=="nst[0-9]", SUBSYSTEMS=="scsi", ENV{ID_SERIAL}=="", IMPORT{program}="scsi_id -g -x -s %p -d $tempnode"
KERNEL=="nst[0-9]", SUBSYSTEMS=="scsi", ENV{ID_SERIAL}=="", IMPORT{program}="scsi_id -g -x -a -s %p -d $tempnode"
KERNEL=="nst[0-9]", SUBSYSTEMS=="scsi", ENV{ID_SERIAL}=="?*", SYMLINK+="tape/by-id/$env{ID_BUS}-$env{ID_SERIAL}-nst"

# type 8 devices are "Medium Changers"
KERNEL=="sg*", SUBSYSTEMS=="scsi", ATTRS{type}=="8", ENV{ID_SERIAL}=="", IMPORT{program}="scsi_id -g -x -s %p -d $tempnode"
KERNEL=="sg*", SUBSYSTEMS=="scsi", ATTRS{type}=="8", ENV{ID_SERIAL}=="", IMPORT{program}="scsi_id -g -x -a -s %p -d $tempnode"
KERNEL=="sg*", SUBSYSTEMS=="scsi", ATTRS{type}=="8", ENV{ID_SERIAL}=="?*", SYMLINK+="tape/by-id/$env{ID_BUS}-$env{ID_SERIAL}"

SUBSYSTEM!="block", GOTO="persistent_storage_end"

# skip rules for inappropriate block devices
KERNEL=="ram*|loop*|fd*|nbd*|gnbd*", GOTO="persistent_storage_end"

# never access non-cdrom removable ide devices, the drivers are causing event loops on open()
KERNEL=="hd*[!0-9]", ATTR{removable}=="1", DRIVERS=="ide-cs|ide-floppy", GOTO="persistent_storage_end"
KERNEL=="hd*[0-9]", ATTRS{removable}=="1", GOTO="persistent_storage_end"

# never add uuid information for whole disk
ATTR{whole_disk}=="", GOTO="persistent_storage_end"

# for partitions import parent information
KERNEL=="*[0-9]", IMPORT{parent}="ID_*"

# by-id (hardware serial number)
KERNEL=="hd*[!0-9]", IMPORT{program}="ata_id --export $tempnode"
KERNEL=="hd*[!0-9]", ENV{ID_SERIAL}=="?*", SYMLINK+="disk/by-id/ata-$env{ID_MODEL}_$env{ID_SERIAL}"
KERNEL=="hd*[0-9]", SYMLINK+="disk/by-id/ata-$env{ID_MODEL}_$env{ID_SERIAL}-part%n"

KERNEL=="sd*[!0-9]|sr*|st*", ATTRS{ieee1394_id}=="?*", ENV{ID_SERIAL}="$attr{ieee1394_id}", ENV{ID_BUS}="ieee1394"
KERNEL=="sd*[!0-9]|sr*|st*", ENV{ID_SERIAL}=="", IMPORT{program}="usb_id -x"
KERNEL=="sd*[!0-9]|sr*|st*", ENV{ID_SERIAL}=="", IMPORT{program}="scsi_id -g -x -s %p -d $tempnode"
KERNEL=="sd*[!0-9]|sr*|st*", ENV{ID_SERIAL}=="", IMPORT{program}="scsi_id -g -x -a -s %p -d $tempnode"
KERNEL=="sd*[!0-9]|sr*", ENV{ID_SERIAL}=="?*", SYMLINK+="disk/by-id/$env{ID_BUS}-$env{ID_SERIAL}"
KERNEL=="sd*[0-9]", ENV{ID_SERIAL}=="?*", SYMLINK+="disk/by-id/$env{ID_BUS}-$env{ID_SERIAL}-part%n"

KERNEL=="mmcblk[0-9]", ATTR{name}=="?*", ATTR{serial}=="?*", ENV{ID_NAME}="$attr{name}", ENV{ID_SERIAL}="$attr{serial}", SYMLINK+="disk/by-id/mmc-$env{ID_NAME}_$env{ID_SERIAL}"
KERNEL=="mmcblk[0-9]p[0-9]", ATTR{name}=="?*", ATTR{serial}=="?*", ENV{ID_NAME}="$attr{name}", ENV{ID_SERIAL}="$attr{serial}", SYMLINK+="disk/by-id/mmc-$env{ID_NAME}_$env{ID_SERIAL}-part%n"

# by-path (shortest physical path)
KERNEL=="*[!0-9]|sr*", IMPORT{program}="path_id %p", SYMLINK+="disk/by-path/$env{ID_PATH}"
KERNEL=="st*", IMPORT{program}="path_id %p", SYMLINK+="tape/by-path/$env{ID_PATH}"
KERNEL=="sr*|st*", GOTO="persistent_storage_end"
KERNEL=="*[0-9]", ENV{ID_PATH}=="?*", SYMLINK+="disk/by-path/$env{ID_PATH}-part%n"

# by-label/by-uuid (filesystem properties)
KERNEL=="*[!0-9]", ATTR{removable}=="1", GOTO="persistent_storage_end"
IMPORT{program}="vol_id --export $tempnode"
ENV{ID_FS_USAGE}=="filesystem|other|crypto", ENV{ID_FS_UUID}=="?*", SYMLINK+="disk/by-uuid/$env{ID_FS_UUID}"
ENV{ID_FS_USAGE}=="filesystem|other", ENV{ID_FS_LABEL_SAFE}=="?*", SYMLINK+="disk/by-label/$env{ID_FS_LABEL_SAFE}"

# BIOS Enhanced Disk Device
KERNEL=="*[!0-9]", IMPORT{program}="edd_id --export $tempnode"
KERNEL=="*[!0-9]", ENV{ID_EDD}=="?*", SYMLINK+="disk/by-id/edd-$env{ID_EDD}"
KERNEL=="*[0-9]", ENV{ID_EDD}=="?*", SYMLINK+="disk/by-id/edd-$env{ID_EDD}-part%n"

LABEL="persistent_storage_end"

-----------------------------------------------------
/etc/udev/rules.d/60-libpisock.rules': No such file or directory

This should not prevent booting. I believe you deleted the file, but a script elsewhere still refers to it. Re-installing the Palm Pilot packages should put in a correct file.

----------------------------------------------------

When all else fails, you can try moving non-essential files somewhere else for a while. If moving it prevents booting, then you just have to fix it. If not, you can fix it later, or re-install the problem package to update the file.

---

### Post by James Keating on 2007-05-10
Rats, this is a Mac forum? I hadn't noticed when replying. My suggestions should still work, but the specifics in the files may be quite different.

---

### Post by mrqwa on 2007-05-10
i´ve solved all the errors, and now.. it still doesn´t continute:( 
my screen goes like this::

> * Activating swap
* Checking root file system…
fsck 1.40-WIP (14-Nov-2006)
/dev/hda3: clean, 218730/4931584 files, 9239843/9849609 blocks

* Checking file systems…
fsck 1.40-WIP (14-Nov-2006)

and then... nothing. system stops booting.
i don´t understand....... thanks a lot

---

### Post by sent17inel on 2007-06-18
Umm

---

### Post by r0cks0ul on 2007-06-20
Well it seems nobody was able to fix the problem....
Same problem I had....
So should I reinstall a fresh copy by now?!

Definitely......

****When everything fails there is always a way to fix it***
[IMG]http://i95.photobucket.com/albums/l158/r0cks0ul/vistalaunching2.jpg[/IMG]

---

### Post by PrimozKajdo on 2007-08-01
HI!

So, I guess I have the same problem as all of you. I tried to fix the files in the /tec/event.d and I did so with ttyX files and with control-alt-delete, logd and sulogin.

My question is - what about rcX files? Can anyone put online an example of those files? 
in rc0 I have a line that says
exec /etc/init.d/rc 0

and it is followed by
end script

shoud it not be followed by "respawn"?

and another question - some say that putting the "nosplash" option in the menu.lst they get these messages that tell them the errors. Where exactly and how exactly does one use the nosplash option?

cheers

primoz

---

### Post by kfchoo on 2007-12-10
Give up on Ubuntu! Move to other distribution.! 

Ubuntu basically is worst than Microsoft Window!

Keep up the worst work~~

---

