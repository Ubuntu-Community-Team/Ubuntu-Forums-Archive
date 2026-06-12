---
title: "i read too much :("
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by Jbirdie1 on 2006-03-22
i want to take 6 months to understand ubuntu, so i can ditch all microsnot products when vista comes out. but, i have read too much about 'dual boot' xp and ubuntu. can i just resize the freespace on the windows drive, then take care of the formatting as part of the install process?!?!?!?

heres the deal - drive c:\ 20gb ntfs (no change for linux), drive d:\ 80gb ntfs (system fles only, NO o/s) ---plan to take approx 18gb of drive d: and allocate it for linux

---

### Post by aysiu on 2006-03-22
6 months. Wow.

I would play around with a live CD for a couple of weeks--get the hang of the interface, see how the hardware detection is.

If you're still sure you want to install a dual-boot, use this guide:
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

---

### Post by Shampyon on 2006-03-22
I'm taking that approach, too. Dual booting with XP and giving myself a goal of 6 months to understand how to get Ubuntu to do all the things I want it to. I've had problems with the install I never had with the Live CD. You'll probably notice some difficulties if you have an ATI card, though these are (for the most part) easily overcome. If you have a Sound Blaster Audigy sound card, you may have some difficulty too. Once again, this is pretty easily overcome.

I'm not sure, but if you're planning on sharing a partition between Linux and XP, you'll be better off using FAT32 than NTFS. Makes it easier to read, since Linux in general is still getting used to NTFS.

Say, for example, NTFS for your Windows Partition, FAT32 for the partition used by both XP and Ubuntu, and whatever FS you choose for the Ubuntu partition (I'm using ReiserFS).

---

### Post by az on 2006-03-22
[QUOTE=Jbirdie1]. can i just resize the freespace on the windows drive, then take care of the formatting as part of the install process?!?!?!?
[/QUOTE]
You don't even have to do that.  The installer will scan your hardware and ask you if you want to install ubuntu on
1.  Whatever free space is on the first hard drive (it can shrink the windows partition for you)
2.  All of the first drive (wipe it out)
3.  Whatever free space is on the second hard drive (again, it can shrink it)
4.  All of the second drive.

You chose.  What you want is option three.  The installer uses very very reliable partitoning tools.  That's no excuse to not back up your data, but there seem to be a lot fewer problems with partitioning using the linux tools than using proprietary windows tools.

---

### Post by pchr on 2006-03-22
[QUOTE=azz]That's no excuse to not back up your data, but there seem to be a lot fewer problems with partitioning using the linux tools than using proprietary windows tools.[/QUOTE]

I'd agree with that.  I hosed my computer using Partition Magic.  I didn't know the Ubuntu install CD had it's own partitioner.  

Not a big deal though when you've written all your mp3s, photos and other docs to 5 or 6 DVDs before you started.  :-\"

---

### Post by Sef on 2006-03-22
> I hosed my computer using Partition Magic

There are a lot of posts about problems with using PM.

---

### Post by brandoncolorado on 2006-03-22
PM worked really well for me.

I had to 
1) Resize windows partition
2) Move it for the 500mb Linux wanted
3) Make a partition for Linux

There was one glitch and XP wouldn't boot, but it was easily fixed by editing a line in GRUB.

---

### Post by caffinide on 2006-03-22
[QUOTE=Jbirdie1]6 months[/QUOTE]

Geez, I can't even focus for 6 minutes... 6 months, thats a lot of time

---

### Post by az on 2006-03-22
[http://www.ubuntuforums.org/showthread.php?t=119388&highlight=partition](http://www.ubuntuforums.org/showthread.php?t=119388&highlight=partition)

---

