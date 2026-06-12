---
title: "I am not enttitled to mount external drive now. (oh yes I am!!)"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by jnorris235 on 2008-01-06
External USB hard drive I use for backups - suddenly today I'm told I'm not privelidged to mount it.
Why not? What have I done to be punished in this way?

I did SEARCH - one reply told me to do something and I got this warning:

>>WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.<<

So please tell me in plain english what to do?

Here is my fstab file (esoteric stuff, but I found it!) in case it is relevant.
I can open it but if I try and do anything in it it tells me I don't have permission!
Is there no way to open it WITH permissions without fiddling with the console?

The one thing I hate most about Ubuntu is the way things work one minute and then don't the next. (small rant)

>>
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=89c6d7b0-dddc-4296-ba02-3d85363bac46 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=d6d2df5a-0afa-40a4-a160-d54d980b884f /home           ext3    defaults        0       2
# /dev/sda2
UUID=756cc1dd-c9b9-43b6-8548-0a6d02e3539e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb1 /media/disk vfat iocharset=utf8,umask=000 0 0
<<

This line got there somehow when I tried to format my chinese ipod. No luck there either!!
Thank you - hopefully ...

---

### Post by The Cog on 2008-01-06
What makes you say you are not enttled to mount it? How do you try to mount it, and do you get some kind of error message?

The fstab listing may well prove helpful, thanks.

---

### Post by jnorris235 on 2008-01-06
After phoning someone I was forced (!!) to type into the Konsole 'sudo kate' and I deleted the last line of fstab (which was someone trying to enable me to mount, see and format my chinese ipod - never worked!!).

Then my external hardrive came back happy.

Ages ago I had Kubuntu and you could edit things happily in Kate by providing the sudo password. Not in Ubuntu - can only get at it via Konsole it seems.

Sorry for taking your time - thanks for helping.

In answer to your question - a box came up telling me I was underprivelidged. Imagine if it said that on a £50 laptop tp REAL underprivelidged people!

---

### Post by nowshining on 2008-01-06
does a password box come up asking for a password - if so - then input ur password.

as for kate

just sudo kate (intall it first), or gedit (defualt for gnome)

or gksudo them and input ur pw.

then once opened up in sudo browse to the file u want to edit and open it, and u could also sudo gedit and the location of the file then input ur pw and it opens up in gedit.

---

### Post by jnorris235 on 2008-01-06
Yes - thanks.
I was assuming you could open gedit from the menu AND save things without having to sudo gedit in Konsole.

Why can't you save, and instead of it just refusing, it could ask for a password?
I'm sure kate used to do that in kubuntu.

I don't think I'll ever get my family off Windows whilst these difficulties exist!
Cheers all.

---

