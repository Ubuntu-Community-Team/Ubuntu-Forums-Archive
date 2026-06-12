---
title: "deleting  ubuntu partition from macbook 4,1 ( refit bootloader)"
date: 2009-12-21
forum: Apple Hardware Users
---

### Post by mackaframa85 on 2009-12-21
I'm about to sell my white macbook 4,1 and I need to delete the ubuntu partition to please the buyer.  It uses refit as the boot loader, but I'm afraid to just delete the ubuntu partition. What are the steps invloved in this process.

Thanks for any help in advance!

---

### Post by Grenage on 2009-12-21
I would personally boot from an ubuntu live CD, run gparted and delete the partition from there.  You can then expand the existing partition(s) to make use of the room.

---

### Post by mackaframa85 on 2009-12-21
> **Grenage said:**
> I would personally boot from an ubuntu live CD, run gparted and delete the partition from there.  You can then expand the existing partition(s) to make use of the room.
   Is there a tutorial anywhere which explains this?? By the way I'm running ubuntu 8.10 intrepid ibex!

---

### Post by Grenage on 2009-12-21
Unfortunately I am currently on a limited connection at this moment, so I can't search and find you one.  It is however really simple.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Download that, burn it and boot it.  Really easy interface.

---

### Post by tom4everitt on 2009-12-22
Actually, you can just boot your ubuntu live cd.

Go to Applications -> System Tools -> Gparted disk manager

(or something similar). 

Once there its a piece of cake removing partitions.

To please a buyer I would suggest you do a fresh install of os x, where you before you start the installation process open disc utility and reformat your hard drive (make one big os x partition only). This will make the computer feel brand new :) ...will even give the buyer the nice welcome intro and stuff.

---

### Post by Grenage on 2009-12-22
Indeed; I merely suggested the gparted disk because it is 30MB rather than 700.

---

### Post by mackaframa85 on 2009-12-22
> **tom4everitt said:**
> Actually, you can just boot your ubuntu live cd.

Go to Applications -> System Tools -> Gparted disk manager

(or something similar). 

Once there its a piece of cake removing partitions.

To please a buyer I would suggest you do a fresh install of os x, where you before you start the installation process open disc utility and reformat your hard drive (make one big os x partition only). This will make the computer feel brand new :) ...will even give the buyer the nice welcome intro and stuff.
 
This sounds like an awesome option! How do I go about doing this? that is reformat the harddrive and make one big osx partition only

---

### Post by tom4everitt on 2009-12-23
> **mackaframa85 said:**
> This sounds like an awesome option! How do I go about doing this? that is reformat the harddrive and make one big osx partition only

Piece of cake:

Just put your os x install dvd into the cd driver, reboot and hold down c while its booting, so you get into the installer. 

Once in the installer you will find disk utility in the top menus. 

In disk utility you click on the hard drive in the left column (not on one of the partitions), go to partitions, erase all the current partitions, create one big one. File system should be journaled hfs+, which is the default one. 

Install os x as normal. 




One thing to know before you go ahead though is that if you have a snow leopard upgrading dvd, and not the full install dvd, it won't let you install snow leopard on an empty disc. In this case you need to install your old os x system first, and then upgrade.

---

### Post by wheredidrealitygo on 2009-12-23
> **tom4everitt said:**
> 
One thing to know before you go ahead though is that if you have a snow leopard upgrading dvd, and not the full install dvd, it won't let you install snow leopard on an empty disc. In this case you need to install your old os x system first, and then upgrade.

Snow Leopard clean installed (from a blank, entirely repartitioned hard drive) on my Macbook 5,1 from an 'upgrade' dvd just fine.

---

