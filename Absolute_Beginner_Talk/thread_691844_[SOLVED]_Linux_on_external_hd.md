---
title: "[SOLVED] Linux on external hd"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by hovzio on 2008-02-09
hi, just installed ubuntu 4 weeks ago and windows has run about 20 min since then :).  I installed ubuntu on an external drive on my laptop. Vista is on the internal hd. Im having some booting issues id like to fix, Grub dosnt start if i dont have the external hd pluged in, so basically without my external drive i cannot boot to vista. It sais grub error 21.if i have the ext. hd plugged in it works fine. Im a newbie but my guess is that grub is installed on my ext hd. I mean its not the end of the world but if i wanna use windows i need my external drive to boot. is there anyway around this, did i install ubuntu in an improper way? Also,** what happens if i need to reinstall windows**?im sure it will reset the mbr and ill be able to access windows as usual but i think i wont be able to get to ubuntu...what does grub do to my mbr?so many questions....

---

### Post by eggdeng on 2008-02-09
Presumabably you installed GRUB to it's default location, the MBR (first sector, first hard disk) overwriting the MS bootloader. However, GRUB keeps some of it's files on the Ubuntu partition, so it won't boot without that partition present. 
Reinstalling W*nd*ws would have the effect you suggest so you would have to reinstall GRUB (using the Super Grub Rescue Disc).
It would have been better to have shrunk the W*nd*ws partition and have installed Ubuntu alongside W*nd*ws, leaving the external drive free for storage.

---

### Post by hovzio on 2008-02-09
alright, i like the idea of putting ubuntu and ms on the same hd, but can i still use my recovery disk for vista then (using a toschiba laptop). dont know quite how to formulate the next question but i know that ubuntu runs on ext3 and windows on ntfs, arent there any conflicts with this even if they are seperate partitions.

---

### Post by eggdeng on 2008-02-09
> ubuntu runs on ext3 and windows on ntfs
Most of us dual boot using these two filesystems & without problems. W*nd*ws won't recognise the ext3 partition but you can read and write from Ubuntu to the W*nd*ws partition once you enable ntfs3g.
As for the recovery disk, in my experience this is a lethal weapon which is only good for blindly formatting and overwriting everything with a naked W*nd*ws install. By rights, you should have been given a full installation disk when you paid for the system, but then MS wouldn't have you by the b**s.
You can find a complete discussion of the issues at [https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

---

### Post by hovzio on 2008-02-10
thanks for the help, i think i got it all figured out. The ubuntu forums are great, i have a question, it is answered and i recieve immediate help. Im new to ubuntu and have been using ms for years and never got any support when i need it. Fact is i rareley need help with ubuntu, it runs far better than ms...I want to thank all involved in the open source community, the people involved are making an active difference in todays monopolistic world.

---

