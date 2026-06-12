---
title: "Edgy will not boot after Windows install"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by garyed on 2007-08-03
My Grub menu comes up & it will let me get into Win XP but it will not let me into Ubuntu.
I get this message:

/bin/sh: can't access tty: job control turned off
(initramfs)
Anyone know what that means & how to fix without a reinstall.

I was running Win98 on one HD & Edgy on the other & dual booting fine.
I reformatted my Windows drive(C) & installed XP.
Then I booted to the Ubuntu 6.10 CD  & got to the terminal & did the commands:
sudo grub
find /boot/grub/stage1        "   Which returned (hd1,0) "
root (hd1,0)
setup (hd0)       
quit

The only thing unusual was the computer locked up shutting down.
I've done this before without a problem but this time it looks like something happened to my Ubuntu startup files.

Any clues?

---

### Post by asmoore82 on 2007-08-03
using grub to dual boot off of 2 different drives is sort-of pointless when the LinuxOS
that houses GRUB's stage2 and config files is not on the Primary Master Drive.

having said that; that is what all dual-booters seem to want to do.
they intentionally, for reasons that escape me, create a setup whereby
Winders will not be readily bootable if/when the Linux partition gets deleted/moved/damaged.

anyways, your setup will probably work if you do the same setup again and end it with
'setup (hd1)' then tell your BIOS to boot from the Linux drive.

---

### Post by Glake on 2007-08-03
I had a problem similar to that. I have hda used for Ubuntu and hdb2 used for Windows XP.

I installed XP after Ubuntu and then ran into a few problems.

So I had to reinstall Grub, got the info I needed from this post,

[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)


After that I had a hard time since XP was on hdb2, it didn't want to boot because it wasn't on hda. So I found some info and made a few changes in my /boot/grub/menu.lst for Windows XP, (those two map lines make XP think it is booting from hda instead of hdb.)

title Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
root (hd1,1)
savedefault
makeactive
chainloader +1

I am not sure if this helps at all, hope it does or at least gives you some ideas.

---

### Post by garyed on 2007-08-03
Does it matter that I used the 6.10 installation CD?
I keep hearing Live CD, is that something  different?
Could that be my problem?

---

