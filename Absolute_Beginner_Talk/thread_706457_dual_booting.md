---
title: "dual booting"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by oscarthefish on 2008-02-24
I have reinstalled Ubuntu 7.10 and really enjoy learning all about the OS but can anyone tell me how i might install Fedora 8 and dual boot? Any help or advice is really appreciated. Thanks all.

---

### Post by Tyke91 on 2008-02-24
the fedora 8 live cd installer comes with a partition manager, shrink your ubuntu partition down and install fedora in the new space. Set swap to the same partition you are using in ubuntu. You may be able to set /home as the same thing as well, but I'm not sure.

fedora will automatically re-install grub on your machine, so you will automatically be able to dual boot.

---

### Post by wolfen69 on 2008-02-24
use the gparted live cd or parted magic to resize your partition. then install fedora to the newly created free space.

---

### Post by Duck2006 on 2008-02-24
Use gparted to make the space for the / root for fedora. Then install fedora using the newe ? space for the root and it will use the same swap as ubuntu. Then when it comes to the loader use ubuntu or fedora witch ever one you want to boot the system. If you use ubuntu you will have to add the lines to boot fedora with.

---

### Post by oscarthefish on 2008-02-24
Have never attempted to dual boot two Operating Systems before nor have i ever used GParted either. Looks a bit complicated to me.

---

### Post by Duck2006 on 2008-02-24
This is where you can get gparted from.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

and this one is for pmagic

[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

Both have Documentation pages as to how to.

---

### Post by Forrest Gumpp on 2008-02-24
Have a read of Herman's Illustrated Dual Boot Site.  The home page is:  [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

The page with the detail you are interested in is:  [http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning](http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning)  Scroll down to the bottom of the page to the heading 'Windows and Linux multiple boot arrangements'.

Also read the links Herman supplies in the partitioning page to aysiu's site.

---

### Post by oscarthefish on 2008-02-24
Hey big thanks for all the links guys!

---

### Post by -random on 2008-02-24
after installing, fedora will have formatted it's "/" root partition, so when you boot into ubuntu you'll probably get a message telling you to "ctrl + D to resume boot".

then type ctrl + D,
once in ubuntu open terminal and type:
blkid
then open another terminal and type:
sudo gedit /etc/fstab
and change the UID of the partition (probably something like sda0 or sda1 or sda2 or something) to match.

---

