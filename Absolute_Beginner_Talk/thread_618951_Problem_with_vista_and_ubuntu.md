---
title: "Problem with vista and ubuntu"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by Deepak_007_bond on 2007-11-21
Hello buddie's..

Now here's wat i did...

I had Vista on C:drive and later installed ubuntu. i was able to dual boot both easily.
  
    And later again i installed afresh copy of Vista on C drive. Now Ubuntu is not on my Boot screen. And The D: drive on which i had Ubuntu was of 20GB space and now it shows only 10GB.

   What have i done??:confused:  And wat can i do to get back my Ubuntu and 10GB back????

---

### Post by p_quarles on 2007-11-21
By reinstalling Windows, you overwrote the master boot record, and deleted the program that loads Ubuntu. The good news is that it's easy to fix. Here's a tutorial:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

P.S. Requests like this should go in the "Absolute Beginner Talk" or "General Help" sections of the forums, and this post will be moved there soon by the staff. Just so you know. :)

---

### Post by mouseboyx on 2007-11-21
You rewrote the grub bootloader with the one that boots windows vista

Just re install grub:
download super grub
[http://forjamari.linex.org/frs/download.php/775/super_grub_disk_0.9673.iso](http://forjamari.linex.org/frs/download.php/775/super_grub_disk_0.9673.iso)
Burn the iso image to a cd just like ubuntu and boot it just like ubuntu.

It is pretty straightforward.

---

### Post by Deepak_007_bond on 2007-11-21
Thank u people...
I will try.

---

