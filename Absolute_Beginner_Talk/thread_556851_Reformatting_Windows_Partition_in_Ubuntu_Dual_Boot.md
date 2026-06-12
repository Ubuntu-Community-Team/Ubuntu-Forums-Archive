---
title: "Reformatting Windows Partition in Ubuntu Dual Boot"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by axiomata on 2007-09-21
I've had windows XP and Ubuntu dual booting on my machine for a while now, and Ubuntu is working great, but windows is doing what it does best and pleading for a format and reinstall.

I just wanted to make sure this process wouldn't mess anything up in Ubuntu or Windows.  Both OSs are on the same HD, XP on c: and Ubuntu on another partition.

If I put my Windows install disc in my drive, boot from that CD, format my c: drive, then install windows in that newly created space would you anticipate that I have any problems?

Thanks

---

### Post by oilchangeguy on 2007-09-21
> **axiomata said:**
> I've had windows XP and Ubuntu dual booting on my machine for a while now, and Ubuntu is working great, but windows is doing what it does best and pleading for a format and reinstall.

I just wanted to make sure this process wouldn't mess anything up in Ubuntu or Windows.  Both OSs are on the same HD, XP on c: and Ubuntu on another partition.

If I put my Windows install disc in my drive, boot from that CD, format my c: drive, then install windows in that newly created space would you anticipate that I have any problems?

Thanks

back up your data (on both os's) reinstall windows, then use the live ubuntu cd to reinstall grub.

---

### Post by JacobSteelsmith on 2007-09-21
No, it won't be. Grub will be overwritten by the Windows installer. 

Read [http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/) for more information on how to restore grub.

---

### Post by alienexplorers on 2007-09-21
You can find instructions to load grub in my sig line.

---

### Post by Pumalite on 2007-09-21
To re-install Grub you can use this too:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Or Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by axiomata on 2007-09-21
OK thanks for the help.

Just a question for my own knowledge...

When you have Windows installed and then you install Ubuntu to be dual booted, upon boot, since Ubuntu was installed second, your system tries to boot it first but Ubuntu is "nice" and directs you to GRUB so you can choose which OS you want to boot.

But when you install Windows after Ubuntu is already on your system it doesn't "play nice" and assumes whenever your system is rebooted that you want Windows to boot.

Is that a correct way of looking at it in simple terms?
---

Also, it appears I was wrong as far as the partitioning of my harddrives (I think I changed it at one point.)

My Disk 0 has my C: WindowsApps first, then some unknown 8mb partion not sure what it is.
My Disk 1 has my D: WindowsDocuments first (I forgot how I did it but I changed where My Documents were stored ... will have to look that up), then a healthy active partion (Ubuntu), then a 510MB Healthy Unknown (Ubunut page file I think), and then a partition of FAT32 storage that both windows and ubuntu can recognize.

My question is the link says to 
>     sudo grub

    > root (hd0,0)

    > setup (hd0)

    > exit


Any idea of how I ought to alter that for my particular setup?

---

### Post by Duck2006 on 2007-09-21
To setup grub for your ubuntu root partition where the menu.lst is the grub setup sould read as 

 sudo grub

> root (hd1,0)

> setup (hd0)

> exit

---

