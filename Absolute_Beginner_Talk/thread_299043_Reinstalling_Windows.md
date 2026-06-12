---
title: "Reinstalling Windows"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by spenny on 2006-11-13
I have successfully installed Ubuntu on the second hard drive of my PC and have been using it for several weeks now. I have upgraded to Edgy and so far everything is hunky dory.

On my first hard drive I have Windows XP Professional installed, but it's becoming horribly slow. What I want to do is erase it and do a fresh install of XP Home.

I'm worried though that somehow Ubuntu will be lost (i.e. GRUB won't be recognised).

Am I worrying for no reason or is there a way to go about this safely? I know they recommend you install Windows first then Ubuntu, but I can't seem to find any documentation on doing it the other way round. 

Any help would be most appreciated.

---

### Post by bulldog on 2006-11-13
Where is GRUB installed ie. which disk are you booting from?

The best way to set up dual boot with two hdd's is Ubuntu and GRUB on the boot disk and Windows on the secundary.
So you have GRUB to boot windows and Ubuntu and you can boot windows without grub by selecting the second drive as boot device.

Reinstalling GRUB is a matter of minutes.

---

### Post by spenny on 2006-11-13
> **bulldog said:**
> Where is GRUB installed ie. which disk are you booting from?

Probably on the second (slave) disk, but I'm just guessing.

A whereis grub brings up:

grub: /sbin/grub /lib/grub /usr/share/man/man8/grub.8.gz

so I guess I must be right.

---

### Post by nero2150 on 2006-11-13
[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=grub) 

:cool:

---

### Post by bulldog on 2006-11-13
If GRUB is on the second disk you can reinstall windows without any problem.
If not give a shout and we reinstall GRUB on the Ubuntu disk so you have a clean windows boot loader next to your GRUB.

---

### Post by nickburns on 2006-11-13
Perhaps you could use vmware instead of giving windows a reinstall.  So my thoughts are install vmware, format windows HD to ext3 and run vmware / windows on that hard drive.  This will allow you to use windows and Ubuntu at the same time.

---

### Post by spenny on 2006-11-13
> **bulldog said:**
> If GRUB is on the second disk you can reinstall windows without any problem.
If not give a shout and we reinstall GRUB on the Ubuntu disk so you have a clean windows boot loader next to your GRUB.

Great stuff. I'll give it a whirl.

---

### Post by daverave999 on 2006-11-13
I've got to second nickburns' suggestion of trying out VMware. I installed it a couple of days ago to play poker on and I am most impressed. Unless you are needing Windows for games, as I hear VMware isn't quite up to that.

I will point out VMware Server is FREE, spenny.

---

### Post by spenny on 2006-11-14
Just to provide some closure to this....

Firstly thanks for your help and suggestions.

I booted from the Windows CD, erased the hard drive and did a clean install. No Ubuntu....oh dear.

So I booted from a Live CD went into grub and simply typed

setup (hd0) 

to put the grub loader on the first (main) hard drive.

Voila! Everything was back to normal.

---

