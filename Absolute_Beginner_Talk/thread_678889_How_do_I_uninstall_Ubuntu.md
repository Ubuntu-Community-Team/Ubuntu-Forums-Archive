---
title: "How do I uninstall Ubuntu?"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by dwarner30uk on 2008-01-26
I have no problems with Ubuntu, but I do need to remove it from one of my PC's which i am passing on to another user. Does anyone have a quick "un-install ubuntu" method which I can use please?:confused:

---

### Post by Kilz on 2008-01-26
> **dwarner30uk said:**
> I have no problems with Ubuntu, but I do need to remove it from one of my PC's which i am passing on to another user. Does anyone have a quick "un-install ubuntu" method which I can use please?:confused:

Yes, Stick the restore disk from your computer manufacturer in and let it format and restore windows. This has the benefit of removing any personal info from windows.

---

### Post by Joeb454 on 2008-01-26
Yeah that's all you have to do, pretty easy really.

Unless of course you don't have a restore disk?

---

### Post by Kilz on 2008-01-26
> **Joeb454 said:**
> Yeah that's all you have to do, pretty easy really.

Unless of course you don't have a restore disk?

Then I would format the drive and give a blank pc , windows contains way to much personal info to simply give the old install away.

---

### Post by MikeyXX on 2008-01-26
Yes they are right. Ubuntu isn't a "program" as such, so you can't just uninstall it. You need to remove it from the drive leaving a blank drive or install another OS over top like the original windows that probably came with your computer.

---

### Post by tekguy on 2008-01-26
> **Kilz said:**
> Then I would format the drive and give a blank pc , windows contains way to much personal info to simply give the old install away.

Well if you use the Restore CD from the manufacturer you will wipe it completely clean and have a clean windows install. If you don't have a restore CD a couple of other options would be to get Darik's Boot and Nuke ( [http://dban.sourceforge.net/](http://dban.sourceforge.net/) ) and wipe that machine clean and give it away with no OS. Or you can drop in your Ubuntu CD, do a clean install (let it format the drives), and give the new user a nice new Ubuntu install to play with.

---

### Post by dwarner30uk on 2008-01-26
OK, thanks so far, but the PC is still in the family, but my granddaughter prefers to boot it up into windows. I haven't convinced her to use U yet. So when the machine powers up, the black screen always offers U first, and she has to arrow down to Windows and enter. Is there a way to change the order of booting, so that Windows is 1st?

---

### Post by Hmarroqu on 2008-01-26
[http://ubuntuforums.org/showthread.php?p=2245129](http://ubuntuforums.org/showthread.php?p=2245129)

---

### Post by Kilz on 2008-01-26
> **tekguy said:**
> Well if you use the Restore CD from the manufacturer you will wipe it completely clean and have a clean windows install. If you don't have a restore CD a couple of other options would be to get Darik's Boot and Nuke ( [http://dban.sourceforge.net/](http://dban.sourceforge.net/) ) and wipe that machine clean and give it away with no OS. Or you can drop in your Ubuntu CD, do a clean install (let it format the drives), and give the new user a nice new Ubuntu install to play with.

May I suggest actually reading the previous posts, it isnt that hard there were only 4 of them before my post.

---

### Post by ugm6hr on 2008-01-26
> **dwarner30uk said:**
> I have no problems with Ubuntu, but I do need to remove it from one of my PC's which i am passing on to another user. Does anyone have a quick "un-install ubuntu" method which I can use please?:confused:

Lots of methods here: [http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

> OK, thanks so far, but the PC is still in the family, but my granddaughter prefers to boot it up into windows. I haven't convinced her to use U yet. So when the machine powers up, the black screen always offers U first, and she has to arrow down to Windows and enter. Is there a way to change the order of booting, so that Windows is 1st?

You can edit Grub menu.lst and change the default to Windows:
```
gksudo gedit /boot/grub/menu.lst
```

Then edit a line near the top:
*default 0* needs to be changed to *default saved*
Check near the bottom where the Windows XP entry is, and make sure it says *savedefault* in its entry.

You can also change the time delay to automatically select Windows (default 10 secs) with the line *timeout x* where *x* is the delay in seconds.

So - your choice... Wipe Ubuntu or change default choice to XP.

---

