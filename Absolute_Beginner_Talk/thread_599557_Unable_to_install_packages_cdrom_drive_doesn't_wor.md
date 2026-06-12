---
title: "Unable to install packages: cdrom drive doesn't work"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by Ronni Elken Lindsgaard on 2007-11-01
Hi

For some odd reason after installing ubuntu 7.10 my cd-rom drive won't read anything. It is listed, but when I try reading it it says "mount: special device /dev/scd0 does not exist" I've been trying to find a solution at this forum, but everything is half explained.

I tried commenting out the line in /etc/fstab
```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

But that didn't solve anything (except removing the device)

Advice will be much appreciated :)

---

### Post by Hospadar on 2007-11-01
Do you know if your cd drive is sata or IDE?  If it's IDE you might try changing the first part of that line in fstab to /dev/cdrom (or /dev/cdrom1, or /dev/cdrw, or /dev/cdrw1, or /dev/scd1)

It seems unlikely that that would work as that would mean your drive was improperly deceted, but you can try.  Make sure you back up your fstab first.

Also, if you have an internet connection on the machine, you can at least get installing packages in the meantime if you go into System->Administration->Software Sources, turn on all the repos, and uncheck "installable from cd"

---

### Post by Ronni Elken Lindsgaard on 2007-11-01
> **Hospadar said:**
> Also, if you have an internet connection on the machine, you can at least get installing packages in the meantime if you go into System->Administration->Software Sources, turn on all the repos, and uncheck "installable from cd"

Yeah figured that out by myself luckily :)

I can't tell if it's sata or IDE but it's in a laptop (Zepto Znote 6625WD if that helps) 

I tried changing the first part of the line, but no luck :(

---

### Post by nidelius on 2007-11-02
I have tried to fool around in the fstab file and change every parameter. Is there no way to se if the DVD/CD is detected. like lspci or dmesg or something. I can't get it to work and if I 
'ls /dev/hd*'
'ls /dev/cd*'
'ls /dev/sd*'

the 'ls /dev/sd*' is the onlything to show anything. Also I have looked in the /dev folder for the CDROM but it does not seem to be there.

*EDIT* I have emailed zepto and asked for the modelnumber of the SAMSUNG CD/DVD it thats what you have I will investigate further

---

### Post by Ronni Elken Lindsgaard on 2007-11-02
Sorry to hear I'm not the only one with problems... I hope we can find something out together :)

I was wondering if there was any way to see which driver is loaded in the Live CD, since the live CD reads the cd/dvddrive correctly...?

**EDIT**

I found the model number it's CDDVDW SN-S082H (well don't think you need the first part) tried searching for linux drivers but no luck :(

---

### Post by Laellis on 2007-11-03
That's a known bug on 6625wd. You can go around it by, after having installed Ubuntu of course, setting the Secondary/Slave to None in BIOS, It's in the first tab. Just select it and pick None by pressing +.

This problem was discussed here [http://forum.notebookreview.com/showthread.php?t=160496]("http://forum.notebookreview.com/showthread.php?t=160496")

---

### Post by Ronni Elken Lindsgaard on 2007-11-03
Thanks a lot :D that worked perfectly

/bow

---

### Post by nidelius on 2007-11-03
works great thanks. Anyone know if this effects something else. I've heard that this error is also present in vista and xp so there is some bios problem overall with this laptop

---

### Post by Ronni Elken Lindsgaard on 2007-11-03
Hmmm wonder if it's because of the bios setting that i can't get my soundcard to work.... anyone been able to get the sound working?

---

### Post by nidelius on 2007-11-03
I'm trying maybe you want to help and try. Here is the post [http://ubuntuforums.org/showthread.php?p=3698864](http://ubuntuforums.org/showthread.php?p=3698864)

---

