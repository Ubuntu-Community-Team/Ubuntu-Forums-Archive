---
title: "Simple OS X/Ubuntu Dual-Boot"
date: 2008-03-08
forum: Apple Intel Users
---

### Post by bilboe on 2008-03-08
Hi,
I would very much like to dual-boot Ubuntu and OS X.
I have an internal 80GB hard drive with 30GB free space, and an external 320GB firewire drive, with 2 partitions that I use for backup and storage. I have installed rEFIt, but no matter how many different ways I try to dual boot (with Ubuntu on seperate partitions on  both my internal & external drive)
I CANT GET IT TO WORK!

Now I have started over with a clean slate, and have OS X, my files, and rEFIt.
If anyone could help me with my dual boot, it would be greatly appreciated. (I would like to do it on my external drive, but either way is fine).

Thank You

---

### Post by bcr88 on 2008-03-08
The only way I could achieve getting Ubuntu on my external HD is by installing the /boot partitions on the internal HD. Which actually is not that big of a deal since /boot could be as little as 60 MB (although I would recommend between 80 and 100 MB to leave some extra room). So, in gparted (the Partition Editor on the live CD, under System --> Administration), you could make a small partition at the end of your internal HD (I would recommend using ext2 rather than ext3, because journalling is not necessary on that volume), and whatever partitions you want on your external (/, /home, etc.) Then when you go to install, make sure you choose to set /boot for the small internal partition. You shouldn't evev notice any space lost on your Mac OS X partition.

---

### Post by bilboe on 2008-03-08
OK! Thank you very much, just one question. If i simply make the external partition "/" will that encompass everything else besides "/boot"?

---

### Post by bcr88 on 2008-03-08
> **bilboe said:**
> OK! Thank you very much, just one question. If i simply make the external partition "/" will that encompass everything else besides "/boot"?

Yes it will. Anything you don't specifically set on another partition will go on /. Although I would recommend making /home a separate partition. That way, if you ever need to reinstall Ubuntu, you won't lose your files. (You can use the same /home partition if you ever need to reinstall.)

---

### Post by bilboe on 2008-03-08
Great, thank you VERY much!

Just one LAST question, 

in rEFIt, how do I know which partition to boot up off of?

---

### Post by bcr88 on 2008-03-08
Umm... I'm pretty sure there should be a selection called either Ubuntu, or Linux, with a penguin icon. I used rEFIt a while ago, but now I just use the built-in bootloader (hold down option when you hear the chime when you turn on your computer. It does label any other OS besides Mac OS X as "Windows," but if you only have two OSes, that won't matter. I use it so I can only bring it up when I want to boot into Ubuntu (instead of the menu always coming up). But rEFIt's a good program anyway.

---

