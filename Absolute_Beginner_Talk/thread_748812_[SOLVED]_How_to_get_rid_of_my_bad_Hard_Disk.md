---
title: "[SOLVED] How to get rid of my bad Hard Disk?"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by GoCool on 2008-04-07
**_Background_**
I have two hard disks 40 gb (primary) and 200 gb (secondary). It was a windows xp machine before it crashed. I then switched to ubuntu. While loading ubuntu, it chose to load on the secondary which I thought is fine and allowed it.

Now I came to know for sure that the primary (40gb)  hdd has gone bad and its of no use. But still it is the primary hdd. So some part of grub is in there and then it passes the control to the secondary (200gb) where the ubuntu os is present.


**_My Problem_**
Is there any way I can just remove the 40 gb hdd and make the 200 gb hdd primary without loosing anything? For I really took pains to load many cool programs and configure it to my taste.


**_What I did so Far_**
1. I  removed  the 40 gb hdd and made the 200 gb hdd primary, but it shows the error
"Operating system not found"

2. I removed the 200 gb hdd and just tried to boot from the 40 gb hdd (which any way was the primary), it shows the grub menu and then gives the following error
"Error 22"
I am not sure what error 22 is.

3. But if I leave the setting as it is, that is 40 gb as my primary and 200 gb as my secondary then there is no problem. But I cant do anything with the 40 gb hdd, it doenst even allow to put any thing in there.


Any help on this would be highly appreciated.

---

### Post by InfinityCircuit on 2008-04-07
This is what you want to do:

1. Remove the 40GB hard disk
2. Set up the 200GB as a primary instead of a slave
3. Boot up a LiveCD and follow these instructions: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by twin_57103 on 2008-04-07
[Super Grub]("http://supergrub.forjamari.linex.org/") would probably do the trick, too.  I had the same problem, although on the Linux drive - I used it to repair the Windows MBR (I've replaced the computer, but going to try to make a functional computer out of what's left...).

---

### Post by GoCool on 2008-04-10
Thank you InfinityCircuit for that valuable link, it really helped me.

There was an extra step I did after following the instruction and that is to go to the

/boot/grub directory and edit the menu.lst

I had to edit it to change the default from (hd1,1) to (hd0,1).

Else everytime I boot I get the error 21 and I have to manually edit it to point to hd0,1.

This little change made sure that it booted with hd0,1 as primary.

Thank you twin_57103 for "Super Grub", even though I did not use it, I'll keep it as my reference point for any future use.

---

