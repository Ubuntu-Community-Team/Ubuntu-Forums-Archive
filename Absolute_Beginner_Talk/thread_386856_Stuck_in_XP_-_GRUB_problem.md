---
title: "Stuck in XP - GRUB problem"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by le_vainqueur on 2007-03-17
I have previously installed Ubuntu 6.06, 6.10, and Kubuntu 6.06, and have had no problems getting into both XP and the Linux distro.  I just did a fresh install of Kubntu 6.10, though, and I can only get into XP.  It seems as though grub isn't even loading.  Here is how I installed things:

1st hard drive: XP
2nd hard drive partitions: Kubuntu, Swap, Shared partition.

Both hard drives were installed when I installed Kubuntu, so I though GRUB automatically installed to the MBR in Windows, but it is not loading when I boot up.


Advice?

---

### Post by AtrejuT on 2007-03-17
can you boot a live cd? You should then be able to install grub using something like grub-install if I remember correctly.

atreju

---

### Post by ajgreeny on 2007-03-17
Try this:-

Boot into the ubuntu live CD
open a terminal and run :
command:-
    "sudo grub"

then:
command:-
    "find /boot/grub/stage1"

replace the question marks in the following command with the output of the last command :
command:-
    "root (hd?,?)"
If you have more than one linux install, use the one that you want the grub to run from. [like : root (hdo,1) ,probably]
then:
command:-
    "setup (hd0)"

and
command:-
    "quit"

Reboot  You should now with luck have a working grub.  Good luck.

---

### Post by orb9220 on 2007-03-17
[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)

---

### Post by le_vainqueur on 2007-03-18
> **ajgreeny said:**
> Try this:-

Boot into the ubuntu live CD
open a terminal and run :
command:-
    "sudo grub"

then:
command:-
    "find /boot/grub/stage1"

replace the question marks in the following command with the output of the last command :
command:-
    "root (hd?,?)"
If you have more than one linux install, use the one that you want the grub to run from. [like : root (hdo,1) ,probably]
then:
command:-
    "setup (hd0)"

and
command:-
    "quit"

Reboot  You should now with luck have a working grub.  Good luck.


I tried this, and it resulted in the same effect (booting into XP w/o going into GRUB).  In a previous installation I had my Kubuntu HD as my first hard drive and my XP HD as the second, so arranged them in that way again to see if the result would be any different.  Upon rebooting XP once again booted directly without going to GRUB, so I once again booted from the Live CD, and attempted to follow your commands.

When running "find /boot/grub/stage1" it responded with "Error 15: File not found."   I suppose this makes sense if GRUB is on my second disk with XP in the MBR.  I'm pretty lost...any idea how I can make this work?

---

### Post by le_vainqueur on 2007-03-18
I played around a little and have some interesting results:

When removing the Windows HD, and having the Kubuntu hard drive as the first disk, GRUB loaded, but would not load an OS.

I then reinstalled Kubuntu with the kubuntu HD as the first HD, and XP as the second.  Upon restarting GRUB loaded with both Kubuntu and XP in the list of OS's, but when I tried to select Kubuntu I received this:
> Error 17: Cannot mount selected partition
The same thing happened when trying to log into Recovery Mode

When trying to log into XP I received this error:
> Error 13: Invalid or unsupported executable format

Now I have to use the Live CD just do anything...weird.

---

### Post by ajgreeny on 2007-03-18
I think it is much easier to have windows on the first (primary) disk and ubuntu on the second.  Try swapping them around so windows is on the first disk and has the MBR on it and then try the ubuntu live CD reinstallation again. Don't forget the disk jumpers may need changing to reflect the master and slave disk change.  I think that you will then get the system working as you want it.

If you want windows as the default boot system instead of ubuntu, don't worry about which disk is which, as you can set the default boot from grub later.

I hope this helps, and that this time it works for you.

---

### Post by le_vainqueur on 2007-03-18
> **ajgreeny said:**
> I think it is much easier to have windows on the first (primary) disk and ubuntu on the second.  Try swapping them around so windows is on the first disk and has the MBR on it and then try the ubuntu live CD reinstallation again. Don't forget the disk jumpers may need changing to reflect the master and slave disk change.  I think that you will then get the system working as you want it.

If you want windows as the default boot system instead of ubuntu, don't worry about which disk is which, as you can set the default boot from grub later.

I hope this helps, and that this time it works for you.


That did the trick.  Thanks so much for the help.  I don't understand why I had problems the first time, however, since the hard drives were the same as they are now...Oh well, I guess I must have done something different somewhere, or I wouldn't have run into the problem.

---

