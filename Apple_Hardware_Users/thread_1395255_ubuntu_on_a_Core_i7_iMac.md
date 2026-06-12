---
title: "ubuntu on a Core i7 iMac"
date: 2010-01-31
forum: Apple Hardware Users
---

### Post by vivniko on 2010-01-31
I am trying to install ubuntu on a 2.8 GHz Core i7 iMac 27".  I'd like to dual-boot with Snow Leopard as well.  I successfully installed rEFIt, and it'll show up whenever I start up my computer.  I've tried multiple times booting from multiple versions of ubuntu live CDs.

I've tried both the 32-bit and 64-bit versions of ubuntu 9.10, and even the 64-bit xubuntu.  All of those resulted in a flashing command-line screen while trying to boot ubuntu from the CD.  I left the flashing screen continue for a while, hoping that it would still boot from the disc, but even after 40 minutes nothing happened.
If it helps, here's what was flashing on the screen while trying to boot from the 9.10 64-bit ubuntu disc:

---------------------------------
deb cdrom:[Ubuntu 9.10 _Karmic Koala_ – Release amd64 (20091027)]/ karmic main restricted
Repeat this process for the rest of the CDs in your set.
W: Skipping non-existing file /cdrom/dists/karmic/main/binary-amd64/Packages
W: Skipping non-existing file /cdrom/dists/karmic/restricted/binary-amd64/Packages
 Removing any system startup links for /etc/init.d/apparmor …
     /etc/rcS.d/S37apparmor
(Reading database … 118846 files and directories currently installed.)
Removing gdm-guest-session …
Linux ubuntu 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64

To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)




To run a command as administrator (user "root"), use "sudo <command>".
See "man_sudo_root" for details.

ubuntu@ubuntu`$
---------------------------------

I am still able to run commands, like I just tried typing in "man sudo_root"
and that brought up the manual page for sudo_root, but the screen kept flashing.

The 64-bit version of 8.04 wasn't successful either, but didn't have a flashing screen - it displayed something else on the screen.  This is what was on the screen:
---------------------------------
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
---------------------------------
I was able to input commands.  Unfortunately I am not familiar with much of these commands, so I did not want to experiment much here.

I don't have much experience with installing ubuntu, and I have not tried installing any other operating systems on this computer so far.  Any help or advice is greatly appreciated.  Also, please let me know if any more information is needed.  Thank you.

---

### Post by linuxopjemac on 2010-01-31
I would try with an alternate cd or server version without X. Then when you finally have it running, work your way up with a desktop. You can then try to find a working Xorg.conf. But reading that you don't have a lot of experience, it might not be a good plan. I guess when you wait half a year, more people have tried it and posted information how to achieve this.

---

### Post by ilario73 on 2010-03-17
vivniko, have a look here:

[http://ubuntuforums.org/showthread.php?t=1398282](http://ubuntuforums.org/showthread.php?t=1398282)

---

