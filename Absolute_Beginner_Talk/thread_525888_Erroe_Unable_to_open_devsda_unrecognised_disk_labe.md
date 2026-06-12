---
title: "Erroe Unable to open /dev/sda unrecognised disk label HELP!!!"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by zibeezibeehey on 2007-08-14
I was told that I can use my external hard drive using the ubuntu live cd. I want to move my files from the hard drive to the external drive. So i was told that i need to us gparted to format the external drive to fat32 and thats where im at now.

Either I fix the problem that way or I think i can install ubuntu onto my partitioned hard drive. I just need to figure out how to install it manually so i dont mess with all of my files i want to keep that are on one partition. Ok if anybody can help because ive being going at this since 7am I would be grateful.

---

### Post by jw5801 on 2007-08-14
What filesystem is the external drive? Have you formatted it to fat32? If you want to install Ubuntu onto it then ext3 is the best bet. If you need to be able to mount it in Windows as well then you'll need to use something else. If you just want to be able to mount it in both windows and ubuntu then ntfs is fine. You would need to install the ntfs-3g libraries though: ```
sudo apt-get install ntfs-3g
```
More information please! If you just want to copy some files onto it so you can format your internal drive to install, then you can use whatever filesystem you want.

Also the Ubuntu LiveCD will let you install to whichever partition on your drive you want, as well as resize other partitions (without losing any of your data, of course) during install to find space.

---

### Post by zibeezibeehey on 2007-08-14
Ok windows XP has crashed on me so ive been using the ubuntu live cd. Today i went and bought and external hard drive so that I ca move my files from my internal hard drive to the externl one. However ubuntu live cd will not let me move my files to the ntfs external hard drive for some reason it gives an error.

So I was on here all night getting it fixed someone told me to use gparted and format my external hard drive to fat32 but that wouldnt work, then i was told to format it to ext3. That worked but it still wont let me move my files. So now I want to put it back to ntfs and that wont work. So I now have an external hard drive programmed for linux that wont work with linux.

All I wanted to do from the get go was install linux on my computer in a small partition on my windows xp partition and hopefully it wont hurt the files that I want to keep on my other partition on the internal hard drive. Once thats done I want to move my files to the external hard drive and then reformat my internal hard drive and put linux on it from scratch.

Is any of this possible I need step by step answers, im way to new at this. I tried to instal using a manual partition but it wouldnt work nor did I know how to make it work. PLEASE HELP!!!

---

