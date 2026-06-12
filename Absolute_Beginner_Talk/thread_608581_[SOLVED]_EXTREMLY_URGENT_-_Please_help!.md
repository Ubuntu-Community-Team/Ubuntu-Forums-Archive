---
title: "[SOLVED] EXTREMLY URGENT - Please help!"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by tarchy on 2007-11-10
Okay so earlier today I asked how to partition my HDD so I can put Windows XP as a dual boot on there.

So I used Gparted since a few people suggested it, resized my HDD and made a new partition, then I installed Windows XP on it. I did not have my key so I could not finish the instalation (this may not be the problem) and I restarted, and I could not get onto neither OS.

Okay, so here is a pic of the install thing (i'm on the live cd) which basically implies that I still have all my files and folders, but I can not find them.

If I create a new partition and then install Ubuntu on it, can I move all my folders from the other one and restart over again? I don't mind spending a few days gathering all my programs back, but I have very important documents and stuff on it. 

Please help, any advice is very much appreciated.

---

### Post by tarchy on 2007-11-10
[IMG]http://img457.imageshack.us/img457/9031/screenshotkr5.png[/IMG]

---

### Post by overdrank on 2007-11-10
> **tarchy said:**
> Okay so earlier today I asked how to partition my HDD so I can put Windows XP as a dual boot on there.

So I used Gparted since a few people suggested it, resized my HDD and made a new partition, then I installed Windows XP on it. I did not have my key so I could not finish the instalation (this may not be the problem) and I restarted, and I could not get onto neither OS.

Okay, so here is a pic of the install thing (i'm on the live cd) which basically implies that I still have all my files and folders, but I can not find them.

If I create a new partition and then install Ubuntu on it, can I move all my folders from the other one and restart over again? I don't mind spending a few days gathering all my programs back, but I have very important documents and stuff on it. 

Please help, any advice is very much appreciated.

Hi when you reinstalled windows it overwrote the grub so you will need to install the grub and this link may help
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Good luck!

---

### Post by tarchy on 2007-11-10
> **overdrank said:**
> Hi when you reinstalled windows it overwrote the grub so you will need to install the grub and this link may help
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Good luck!

I'm not sure if this is the problem as I created a new partition and installed WIndows XP on a differen't partition. If I reinstall the grub, will my files still remain?

---

### Post by overdrank on 2007-11-10
> **tarchy said:**
> I'm not sure if this is the problem as I created a new partition and installed WIndows XP on a differen't partition. If I reinstall the grub, will my files still remain?

Yes, you are just reinstalling the grub. Windows uses the MBR (master boot record) and it overwrites the grub so only windows will boot.

---

### Post by tarchy on 2007-11-10
Okay, thanks. I have followed the tutorial and am going to reboot now. Will return shortly and hopefully mark this as solved :)

---

### Post by tarchy on 2007-11-10
You sir, are a genious. Thank you very much. It worked, obviously :P.

---

