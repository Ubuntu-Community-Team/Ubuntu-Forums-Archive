---
title: "Setup"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by p3_Arme on 2008-02-12
I like to install Linux onto my external HD, however, just a few questions.

1. There are files, music etc, on the HD, does this matter? 

2. I am using ATM my partners laptop, (until I have my own) will the install affect the Windows XP install

3. If not, will I still have the option of using Linux at the start up, or will I have to change the command prompt.

4.What use are Screencasts? (I've seen them around and don't know what they do :) could be just me!!

Thanks in advance 

Emma

---

### Post by jordanmthomas on 2008-02-12
1.  As long as you don't install into the partition with all your stuff in it, you'll be fine.  You can use gparted on the Ubuntu CD to free up some space to install into.

2.  Grub will be installed, which allows you to select between Ubuntu and XP at boot-time.  By default, it will boot Ubuntu, but it's simple enough to make XP the default.  Installing Ubuntu on your external hard drive, though, I am not sure if Grub will be put on it or on the laptop's hard drive.  Someone else needs to verify this one.  If it puts it on the laptop hard drive, you'll likely want to install it on your external instead so you can still boot the computer without having the external hard drive plugged in.

3.  See number 2

4.  Screencasts are just videos people take of their computer and turn them into flash videos (or gifs).  They are usually used to show how to do things step by step in a graphical manner.

Hope this helps, and if I didn't clear anything up, please post back and either me or someone else will try to help more.

---

### Post by zozobra on 2008-02-12
You should also note that being an external drive, your computer will need a BIOS with the capability to boot to external/usb devices.

---

### Post by p3_Arme on 2008-02-13
okay that all made sense, Should I partition my external HD?

Would that be a good idea, if so, What programs should I use and will I lose data already on there.

thanks for the help guys

Emma

---

### Post by sigge on 2008-02-13
Short: Yes!

Partiton, with gparted, and resize your current fat/ntfs partition, and make a second linux partition.

Grub can also go on the  external hd, as the bios will look there first... :) That way, the pc will not load even Grub, unless the external hd is present... ;)

---

### Post by p3_Arme on 2008-02-13
Okay silly question :)

I have a 500GB External HD, how much (big) should the partitions be, out of interest?

Thanks again

Emma

---

### Post by sigge on 2008-02-14
Use 20 or 30 gigabyte for Linux. That is more than enough, yet it leaves you space so you won't have to repartition later on.

Godd luck, btw... :)

---

### Post by hyper_ch on 2008-02-14
If you just want test Linux/Ubuntu, don't make it bigger than 20 GB (at first).

By real testing you'll break it most likely, so don't worry about that (I did a couple of reinstalls in the beginning...)... once you are sure you want to use linux, you can then reinstall the whole thing and also make it bigger.

As already pointed out defragt the drive first 2-3 times in windows.

After that resize the drive so that about 20 GB will be unpartitioned.

I wouldn't even partition those 20 GB then and have the ubuntu installed select to use "largest continuous free space".

---

