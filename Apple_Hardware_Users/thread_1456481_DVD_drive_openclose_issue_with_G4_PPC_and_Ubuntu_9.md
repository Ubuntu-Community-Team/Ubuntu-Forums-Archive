---
title: "DVD drive open/close issue with G4 PPC and Ubuntu 9.10"
date: 2010-04-17
forum: Apple Hardware Users
---

### Post by sastusbulbas on 2010-04-17
Hi all,

Trying to get 9.10 running but one problem I have is with the DVD drive.

When I press open the drawer quickly opens and closes in one swift motion, any ideas? When I do manage to wrangle a CD or DVD in nothing happens, so any ideas on getting the drawer to operate properly and getting it to pay back DVD and CD?

This is the machine I have running, Apple Power Macintosh G4 450 DP (Gigabit)

[http://www.everymac.com/systems/apple/powermac_g4/stats/powermac_g4_450_dp.html](http://www.everymac.com/systems/apple/powermac_g4/stats/powermac_g4_450_dp.html)

Due to being unable to get the original graphics to perform with Ubuntu I am currently running an ATI Radeon Mac edition 9200 card.

---

### Post by conal on 2010-04-17
I don't know how to fix the in-out problem with the drawer but the only way I could get my G4 to automatically mount CD's and DVD's was to install Kubuntu and set KDE as the default display manager instead of Gnome.

The CD/DVD recognition thing is a bug that has been discussed several times - if you search through this forum you'll see there are other solutions suggested. However, none of them worked properly for me.

---

### Post by sastusbulbas on 2010-04-19
I have still found nothing in the search to solve the open close drawer issue?

---

### Post by linuxopjemac on 2010-04-20
Use a USB stick....sorry for the stupid answer but Ubuntu is not always working great. You have to be inventive from time to time.

---

### Post by sastusbulbas on 2010-04-21
Sorry that is not the problem.

I have 9.10 as an OS, and with that OS I am having the drawer issue as well as some others.

I used the DVD drive to load the OS onto my hard drive, now that I have the OS my DVD drive does not function, when I press open the drawer opens and closes in one quick motion, when I do manage to insert CD or DVD media nothing happens I cannot listen to CD or watch DVD.

---

### Post by linuxopjemac on 2010-04-22
this is a known tricky bug. 

you might want to try something like:

```
devkit-disks --mount /dev/hdb
```

where hdb is your linked cdrom
you can have a look with:
```
ls -al /dev/
```

and see which device is linked to dvd or cdrom

You could also edit your /etc/fstab to reflect the right device as cdrom, see appended quote
> 
Ok, I found this post because I had the same problem. After seeing "mount: can't find /dev/scd0 in /etc/fstab" and trying the same things as jnmill1234, I realized that using
sudo gedit /etc/fstab, and changing (this was what the line read in mine)

/dev/hdc /media/cdrom0 udf,iso9660 user,noauto

to

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto

it might work, and it did! yay! I just changed hdc to scd0 which is what it was looking for. Food for thought.

BTW this is EXACTLY the reason why I switched to Debian. Such bugs are in Ubuntu since a VERY long time. The developers of Ubuntu neglect the powerpc arch completely.

---

### Post by oswaldkelso on 2010-04-23
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/283316](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/283316)

I remember reading about this bug and a solution but couldn't find the link.

I use eject and eject -t to open and close the tray then assign it to a keyboard short-cut

---

### Post by sastusbulbas on 2010-05-01
Still have this problem but being such a newbie I probably need the sort of guidance a child could understand LOL

---

