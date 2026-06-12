---
title: "Anybody got a PPC / Yaboot / NetBoot guide ?"
date: 2007-07-24
forum: Apple PPC Users
---

### Post by rectagonal on 2007-07-24
Got a tangerine iBook G3 with an apparently busted optical drive. Trying to load xubuntu on it. Using a PowerMac G4 AGP as the dhcp/tftp server from Ubuntu.

Ive gotten so far as it actually loads the ubuntu kernel over the network but fails on the ramdisk. As I understand it, this is an outstanding issue with yaboot and I have to pair down the ramdisk to somewhere under 6mb. Which I will be doing tonight after work. However a few questions...

Im using the files and yaboot config found here : [http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-powerpc/current/images/powerpc/netboot/](http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-powerpc/current/images/powerpc/netboot/)

I assume after the loading the ramdisk it needs to mount mini.iso , yaboot.conf doesnt seem to have any configuration pointing to that iso. Will this happen automagically and if not, how do I specify it ?

Is their an alternate set of files I should be using to load xubuntu, or is their a way I can tell the installer to load the xubuntu meta package instead of the ubuntu one ?

---

### Post by pxwpxw on 2007-07-24
Look at yaboot.conf and preseed in the server cd iso, or the xubuntu alternate cd iso to see how they select no desktop (cli or server install) or xubunu desktop.

With a cli install you can install xubuntu-desktop later. The alternative to a netboot is to place images and an install cd iso on the g3 hard drive (via network or firewire).  I dont know what is the purpose of the "mini.iso", it seems to contain just the same vmlinuz, initrd, yaboot, yaboot.conf as the separate images, so it would seem to be redundant -but I could be wrong there.

---

### Post by tonyr on 2007-07-24
Here's my experience with this very issue: 
[http://ubuntuforums.org/showthread.php?t=423963]("http://ubuntuforums.org/showthread.php?t=423963")

My current favorite guide is:
[http://www.extremetech.com/article2/0,1697,2132837,00.asp]("http://www.extremetech.com/article2/0,1697,2132837,00.asp")

The only files in my tftp server directory are boot.msg, yaboot, yaboot.conf, vmlinux, initrd.img.
Note that I'm using initrd.img, not initrd.gz.  The post I linked above explains why.

- tony

---

### Post by tonyr on 2007-07-24
The clamshell should have a USB port.  You can boot from a Flash (jump, thumb) drive, too, which
is also explained in that article (my current favorite reference).

- tony

---

### Post by rectagonal on 2007-07-24
Thanks for the comments.

Built a smaller ramdisk using cramfs, which allowed netboot to work. Its unpacking the base packages for Ubuntu "server" as we speak, and then ill install xubuntu-desktop.

Excellent excellent advice, thanks to both of you. :)

---

### Post by pxwpxw on 2007-07-25
> **tonyr said:**
> Here's my experience with this very issue: 
[http://ubuntuforums.org/showthread.php?t=423963]("http://ubuntuforums.org/showthread.php?t=423963")

My current favorite guide is:
[http://www.extremetech.com/article2/0,1697,2132837,00.asp]("http://www.extremetech.com/article2/0,1697,2132837,00.asp")

The only files in my tftp server directory are boot.msg, yaboot, yaboot.conf, vmlinux, initrd.img.
Note that I'm using initrd.img, not initrd.gz.  The post I linked above explains why.

- tony

Thanks for 2 very useful links on USB and other booting plus initrd hacking.:)

---

