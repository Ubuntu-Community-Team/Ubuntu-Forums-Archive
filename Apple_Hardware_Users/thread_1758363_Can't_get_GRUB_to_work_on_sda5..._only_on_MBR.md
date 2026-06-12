---
title: "Can't get GRUB to work on sda5... only on MBR"
date: 2011-05-14
forum: Apple Hardware Users
---

### Post by hugo19941994 on 2011-05-14
Hi,

I recently got a second-hand macbok 4,1, and i'm trying to triple boot it. I got OSX and Windows to boot with rEFIt, but Ubuntu won't boot, unless I install GRUB on the MBR, in which case I can't boot Windows.

And if I repair Windows I can't boot back to Ubuntu... and so forth. I have also installed GRUB on the Ubuntu partition (sda5) with no avail. rEFIt will boot to Windows when I select Ubuntu even if GRUB is installed on sda5. Also, GRUB won't show neither Windows or OSX, so installing it to the MBR and disabling rEFIt won't work.

I don't mind using rEFIt and GRUB, or GRUB exclusively, I really don't care. I just want a one step menu to boot in to any of my 3 OSes.

So, my guess is that i'm installing GRUB (via the Live CD) on sda5 the wrong way.

I've read tons of stuff, I tried so many commands and reformated a countless number of times. I have been trying to get this working for 4 days straight.

Can I get any help please?? Thanks!

EDIT:

Nervermind, I finally got it working today following [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

