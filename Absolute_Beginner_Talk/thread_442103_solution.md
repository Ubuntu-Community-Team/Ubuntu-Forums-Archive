---
title: "solution?"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by spanerman on 2007-05-13
after failing dual booting twice...could i just buy a 50gb external HDD and put the ubuntu files and system on and have windows running on my current HDD.....would it be easyer to boot this way? how would i do it? could i swap this HDD between different pcs and jst boot from it easily?

---

### Post by oilchangeguy on 2007-05-13
setting up a dual boot computer is not difficult. found this to help you:
[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html)
it says it was written for a laptop. but that doesn't matter, the setup is the same for a desktop or a laptop.

---

### Post by spanerman on 2007-05-13
ok that helped but can i do it with dual drives??

---

### Post by trishacupra on 2007-05-13
I did this with my laptop and large external hard drive.

I did it the hard way though - it was a comedy of errors, actually.

My initial plan was to have Windows XP and Ubuntu both boot from my laptop's internal hard drive, and use the external hard drive just for data.

But, even after several defrags, WinXP still had files scattered all over the internal drive (which is only 30GB anyway). So, Ubuntu got installed on my external hard drive (along with some partitions for data that I created both before and after the install - another story in itself). But GRUB was installed on the internal drive.

So, when I didn't have the external drive plugged in, GRUB would give an error and I couldn't even boot into Windows. From a portability point of view, if I wanted to take just my laptop with me without the external drive and use WIndows to do something like play a DVD, it wouldn't work.

So, I got the Super GRUB disk and restored the Windows MBR and installed GRUB on the external hard drive. I changed the boot order too, so Ubuntu is on top, and cut down the selection time to 5 seconds.

Now, when I turn on my laptop without the external hard drive turned on, it boots directly into Windows. But if the external drive is on, it boots straight into Ubuntu.

Good luck with it!

Oh, I also had to change my boot order in BIOS to boot the external drive first, If I turn the laptop on without the external drive on (to use Windows, or by mistake) I have to fix the boot order again next time I turn it on, which is annoying.

Haven't tried plugging the external drive into another PC yet. Hope that works too.

---

### Post by starcraft.man on 2007-05-13
> **spanerman said:**
> ok that helped but can i do it with dual drives??

Yes, I actually find its much easier to have one HDD for all your OS's and then use the other for data storage. I've tried to help a few people install dual boots across two HDDs and they usually get into trouble with the GRUB. Up to you though, thats just my recommendation :)

---

### Post by oilchangeguy on 2007-05-13
sure, i've got mine set up on two internal drives. which is probably easier to set up than using an external drive. why can't you use the single drive in the computer now?

---

### Post by spanerman on 2007-05-13
well i did try to times to partition correctly.......but messed up...im trying again now and i will use 

windows ntfs 20gb
linux ext3     20gb
linux swap    10gb
fat 32   shared the rest about 7 gb

should i use a program in windows to partition it? or the installer? i think a step by step might be usefull......

---

### Post by oilchangeguy on 2007-05-13
why would you have a 10gb swap file? just let ubuntu set it's own partition. allow it to use the largest unused space, and it should split the drive in half. for example 40gb drive will be 20gb to windows and 20gb to ubuntu.

---

### Post by spanerman on 2007-05-13
it didnt give me that option...........only use all or manual....what to do? partition in windows useing a program? whaich one?

---

### Post by spanerman on 2007-05-13
YAAAAAAAAAAAAY i partitions correctly with CPM then booted windows and then linux and it works!!!!!!! thanks for the help

---

### Post by oilchangeguy on 2007-05-13
glad to hear you got it up and running!

---

