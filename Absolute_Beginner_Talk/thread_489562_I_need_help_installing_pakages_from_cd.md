---
title: "I need help installing pakages from cd"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by fjkey on 2007-07-01
I have ubunu 7.04 . It is installed on my desktop. No internet connection there!
I need help : Copying to cdrom,can do that. I'm having trouble installing anything from cd to ?
The last err message that I've got is not diamen disk? I think ubuntu hs recognized cdrom.
I can listen to music,download file to desktop.But cannot install any files! When I got the err message
I was in terminal window trying to get ubuntu to recognize cdrom.

---

### Post by Pragmatist on 2007-07-01
What exactly is your question?

---

### Post by fjkey on 2007-07-01
I need to find out how to install ndiswrapper from cdom? I want to get comfortable installing anything
from cdrom? Can anybody help?

---

### Post by christhemonkey on 2007-07-01
Ok, first off, when your pc is booted up into ubuntu, insert the install cd.

This should then bring up a dialog saying something like "Would you like to add this cd?" Or to that effect.
Click yes.

Then go into synaptic package manager (System >> Administration >> Synaptic Package Manager) and search for ndiswrapper.

Then click to install it.

---

### Post by fjkey on 2007-07-02
Ok mine never promts to run cd. and ndiswrapper doesn't show up in synaptic manager.
It does show up in file brouser.

---

### Post by christhemonkey on 2007-07-02
Ok after inserting the install cd, go into synaptic package manager, click Edit >> Add CDROM.


Then once you have finished adding that cd rom, click reload. And then search for ndiswrapper.

---

### Post by fjkey on 2007-07-02
Thanks for your suggestions,I guess I need to get ubuntu to recognize my cdrom!
it does not on boot.It will not mount from a program! I also have a dvd player( internal)
and it will not mount either.That's probably why I can't Install anything and file to make it work.
I wonder is my hardware not compatable?I have two copy's of ubuntu-7.04 & unleashed 1.0
Cannot get cdrom to mount on either of os's. Also will not recognize my wireless card on either
of them! The strange thing both will play cd music and install files to file browser?
1.They will not install in synaptic package manager.
2. They will not mount or install in the terminal.
3. They will not install in add/remove
Any help? Thanks in advance!
fjkey

---

### Post by Pragmatist on 2007-07-02
Have you tried manually mounting the drive using a terminal?  Please post the output of this command:
```
cat /etc/fstab
```

---

### Post by fjkey on 2007-07-03
# /etc/fstab/:static file system information.
#
# <file system> <mount point>  <type> <options>                  <dump>    <pass>
proc                       /proc                  proc      defaults                       0               0
# /dev/sdal
UUID=acef9178-edd1-440b-bb29-3812ba6607a7 /                       ext3         defaults,err
s=remount-ro  0              1
# /dev/sda5
UUID=9e92682e-d0fc-4d8-81f2-6f92327a8bf2 none                     swap        sw
   0                0
/dev/scd0                 media/cdrom0        udf,iso9660 user,noauto     0       0
/dev/fd0                   media/floppy0        auto     rw,user,noauto      0    0

What do ya think?

---

### Post by Pragmatist on 2007-07-03
Insert a CD, run the following command, and post the output:
```
mount
```

---

### Post by fjkey on 2007-07-03
/dev/sdal on / type ext3 (rw,errors=remount-ro)
proc on /proc type (rw,noexec,nosuid,nodev)
/sys on /sys type sysft (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec ,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /pro/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/ pts type devpts (rw,grid=5,mode=620)
lrm on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw)
binfmt_msic on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

---

### Post by fjkey on 2007-07-03
Also I checked the jumpers on the back of hd & cdrom.
now set hd (master)  cdrom (slave)
Sorry,I really am trying to understand.
I have been reading the book ubuntu unleashed,but so much of it assumes that everything is in working 
order.I would prefer to use this os.To learn something new. But if it is going to cost a whole lot of new
hardware? I remember my dad working in 1982 in dos and  at a slower speed and  not much space.
I guess I would like to use ubuntu and not win.Not because it's free.Because it's different.
Thanks for any help! I will study some,give me some direction.If it is my hardware I will start ubuntu
at a later date.If it is a pieace or two I will replace and keep trying! Tally ho!
fjkey

---

### Post by Pragmatist on 2007-07-03
> **fjkey said:**
> Also I checked the jumpers on the back of hd & cdrom.
now set hd (master)  cdrom (slave)
Is your hard drive IDE, SCSI, SATA?

Normally, you have IDE cables.  The first, IDE 0, is where you connect your hard drives.  The second, IDE 1, is where you connect auxilliary devices such as CD or DVD drives.  Therefore, **you wouldn't put your CD drive on the same cable as your  hard drive**.  If you only have one device on each cable, master and slave is irrelevant.  It only matters--sometimes--if you have two devices on the same IDE port (cable)

---

### Post by fjkey on 2007-07-04
OK my hd is ide.
I put hd on one ribbon & cd on the other.

---

