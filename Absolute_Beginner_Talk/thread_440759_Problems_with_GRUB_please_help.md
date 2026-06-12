---
title: "Problems with GRUB please help"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by river16 on 2007-05-11
Hello, I had to uninstall my ubuntu partition on my xp dual boot machine. So I used gparted to delete the  partition. Now when I boot up GRUB is still trying to start! It gives me an error 22, what is this, and why is GRUB on my machine? More importantly how can I get it off?   Oh yah, I do not have the xp cds, it came loaded with it so there are no cds.

Thanks for any help that you have

---

### Post by phiphedog on 2007-05-12
you need to get your hands on a windows cd and boot into recovery mode and type [COLOR="Red"]fixmbr[/COLOR] and [COLOR="Red"]fixboot[/COLOR] this will fix your master boot record. If you don't have the cd, you may need to beg, borrow or download.

---

### Post by river16 on 2007-05-12
> **phiphedog said:**
> you need to get your hands on a windows cd and boot into recovery mode and type [COLOR="Red"]fixmbr[/COLOR] and [COLOR="Red"]fixboot[/COLOR] this will fix your master boot record. If you don't have the cd, you may need to beg, borrow or download.

do you know where i can download one?

---

### Post by phiphedog on 2007-05-12
I'm certainly not advocating the illegal downloading of copyrighted software but if one was to do it, bittorrent would be the place to start.

---

### Post by confused57 on 2007-05-12
If you have access to another pc, you might want to download & burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

If you don't have access to another computer, you may have to reinstall Ubuntu, then make a copy of SGD, which is able to restore your Window's IPL code to the mbr...then you can delete the Ubuntu partition(s).

---

### Post by river16 on 2007-05-12
okay, so if i were to reinstall ubuntu, how should i repartition my hdd? I deleted the ubuntu one originally so i can not just reinstall:( or can I?

---

### Post by mikewhatever on 2007-05-12
Next time you decide to uninstall Ubuntu, use this page [http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
You can reinstall Ubuntu any time you want too, no limits. However, it seems, you have not yet done it. Is that right? Do you have Ubuntu installation CD?
Just in case, here is the installation guide [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by river16 on 2007-05-12
> **mikewhatever said:**
> Next time you decide to uninstall Ubuntu, use this page [http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
You can reinstall Ubuntu any time you want too, no limits. However, it seems, you have not yet done it. Is that right? Do you have Ubuntu installation CD?
Just in case, here is the installation guide [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

yeah, i wish i had. I dont know why i just assumed that deleting the partition would work. Well i guess i learned the hard way.
yes i do have a cd, should i just make a small partition and install it?  is there any way to save my windows?
anyway, i tried to use supergrub to restore it and it said that it was successful, only problem is that when i try to boot it says that it cant because of  a hardware configuration error.  Any suggestions?

---

### Post by mikewhatever on 2007-05-12
You do not need to reinstall Ubuntu just to be able to use Windows. Super Grub Disk can both boot Windows and to restore its boot loader. There are more tools to do the same, for example [http://www.bootdisk.com/](http://www.bootdisk.com/) Perhaps you could be more specific about the error?

---

