---
title: "Installing via network??"
date: 2005-09-14
forum: Apple PPC Users
---

### Post by MoonDark on 2005-09-14
Hi guys, I want to install ubuntu linux on a iMac G3 , but the CD-ROm is not working...

So I wanted to know if there is some way to install ubuntu via network or something :)

thanks!

---

### Post by GOwin on 2005-09-14
Not directly possible **yet**

From what I've read, the recommended way is to install Debian (Woody is recommended) from floppies or known network boot methods then dist-upgrade to Warty, Hoary or Breezy from there.

---

### Post by Rxke on 2005-09-17
Yes, it is possible, but not for the faint-hearted. If you're a total newbie to Linux, it'll prove a steep learning curve....

OTOH, it's exactly how I got into Linux the first time, some years ago... w/o CD's or floppies, just downloading the Debian images, setting up yaboot, the partitioner... etc... Hours spent reading boards, docs etc... Cursing like mad, all but giving up...

I forgot how i did it exactly, but it had to do something with downloading floppy images, starting up from those, after using partitioner... etc...

And I guess, once you got your base-system running, then just change your sources.list... then update and dist-upgrade... 

Piece of cake for a died in the wool Linux user, several sleepless nights for newbie...
But an interesting excercise!

---

### Post by greyhound4334 on 2005-09-17
You can definitely install from the network.  I posted about a week ago offering to write a howto on this if there was anyone interested, but nobody responded, so I let it drop.  I'm sorry, but I'm on a project now and have to back-burner writing up anything in detail.

But if you're a little linux savvy, you can work it out easily from the source document I worked from here: [http://marc.herbert.free.fr/linux/win2linstall.html](http://marc.herbert.free.fr/linux/win2linstall.html)

Post back if you've got questions after reading the doc and I'll try to answer them.

I did this because I was trying to install on an old PC that wouldn't boot from CD.  It really wasn't very hard.

I would definitely try this approach vs. the debian install and dist-upgrading.  I read about some big problems that some folks had taking that approach, whereas this approach is really a straight ubuntu install.

Good luck!

john

---

### Post by Rxke on 2005-09-17
I did a very quick diagonal scan of the page you linked.

But it's installing via grub, which is no good for an iMac... Beeds yaboot.

(Off again, i'm cooking lunch)

---

### Post by pvz on 2005-09-17
Of course a clean (K)Ubuntu install is nicer, but if you are stuck you could try the Debian route with the Debian-iMac installer from [http://debian-imac.sourceforge.net/](http://debian-imac.sourceforge.net/)
Just install the bare minimum, so say no to installing more packages during installation. This is an old Woody installer, so I really don't know if it is apt-get dist-upgradable to Hoary/Breezy. Maybe upgrade to Debian Sarge first, and then to Hoary/Breezy. Still easier than setting up a netboot environment I suppose. You will probably have to change stable in /etc/apt/sources.list to woody or oldstable to get a working Woody. Anyway, loads of fun guaranteed with this approach :-)

---

### Post by Rxke on 2005-09-17
Ooooh... I wish I had another spare partition handy, just to try this out!
Sounds like 'fun' indeed, if you're into that kind of fun!

(I know I am, heehee...)

---

### Post by greyhound4334 on 2005-09-17
[QUOTE=Rxke]But it's installing via grub, which is no good for an iMac... Beeds yaboot.[/QUOTE]

I really don't know anything about iMacs, so this is completely made up.  But, I'm not sure why this approach is dependent on a specific bootloader.   Basically, you need to download the "install kernel", then boot it.  However you do that on the iMac.  As long as you can choose the kernel to load, select the root filesystem, and pass in parameters to the boot command, it seems like it ought to work.  No?

---

### Post by ninotob on 2005-09-21
[QUOTE=MoonDark]Hi guys, I want to install ubuntu linux on a iMac G3 , but the CD-ROm is not working...

So I wanted to know if there is some way to install ubuntu via network or something :)

thanks![/QUOTE]

Here's how I did it -- it's sort of a terse howto but once you get the basic idea of this, it's actually very easy.  See my post in this thread:  [http://ubuntuforums.org/showthread.php?t=58572](http://ubuntuforums.org/showthread.php?t=58572)

For this you need three things.  The mac on which you will install Ubuntu.  A router that serves of IP address by DHCP.  A linux box to serve up yaboot.  If you want, you can learn how to make the linux box serve up IPs via DHCP -- but that's another thing to learn.  My way is really quite simple.

---

