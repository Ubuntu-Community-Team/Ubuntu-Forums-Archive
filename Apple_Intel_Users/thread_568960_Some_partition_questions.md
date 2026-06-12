---
title: "Some partition questions"
date: 2007-10-06
forum: Apple Intel Users
---

### Post by E Gardner on 2007-10-06
I have a few theoretical questions about partitioning the internal disk of my Macbook Pro (93.2 gb capacity total, marketed as the "80 gb" version since some of the at is automatically set aside for the os x system.

So far I have been splitting this up into:
1. EFI
2. OS X
3. ext3 for ubuntu
4. swap partition for ubuntu

But I am beginning to realize that if I want to be able to use two OSs more effectively, I need a common partition for data that both systems can use easily. So my questions are about how to set this up.

1. The intel macs cannot have more than 4 partitions, right? The swap partition I have right now gets in the way of this. Is there a way to create a swap file within the ext3 partition for Ubuntu to use instead of a separate partition? Also, I have 2GB of ram; is swap even necessary (like for sleep - assuming I can get it to work)?

2. Is FAT32 the best format for a common partition of data here, or are there other options that both hfs+ and ext3 can access easily?

3. I use Thunderbird for email. The advantage of this program is that it runs on both Linux and Mac. Instead of each program creating its own file of all my mail and things (using double the necessary space), is there a way to point each program to a single location that would be on the shared partition? Could it be set up so that, if I worked within one system and downloaded mail, and then went to the other system and opened thunderbird I would see what I had just downloaded? Are there things that have to be done to those annoying "profile" files in order to make this work?

---

### Post by jimrz on 2007-10-06
> **E Gardner said:**
> I have a few theoretical questions about partitioning the internal disk of my Macbook Pro (93.2 gb capacity total, marketed as the "80 gb" version since some of the at is automatically set aside for the os x system.

So far I have been splitting this up into:
1. EFI
2. OS X
3. ext3 for ubuntu
4. swap partition for ubuntu

But I am beginning to realize that if I want to be able to use two OSs more effectively, I need a common partition for data that both systems can use easily. So my questions are about how to set this up.

1. The intel macs cannot have more than 4 partitions, right? The swap partition I have right now gets in the way of this. Is there a way to create a swap file within the ext3 partition for Ubuntu to use instead of a separate partition? Also, I have 2GB of ram; is swap even necessary (like for sleep - assuming I can get it to work)?

2. Is FAT32 the best format for a common partition of data here, or are there other options that both hfs+ and ext3 can access easily?

3. I use Thunderbird for email. The advantage of this program is that it runs on both Linux and Mac. Instead of each program creating its own file of all my mail and things (using double the necessary space), is there a way to point each program to a single location that would be on the shared partition? Could it be set up so that, if I worked within one system and downloaded mail, and then went to the other system and opened thunderbird I would see what I had just downloaded? Are there things that have to be done to those annoying "profile" files in order to make this work?

1.  yes only 4 partitions, but 1 of them can be an "extended partition" which can contain numerous other partitions. Have you already installed ubuntu or just set up your partition table? If already installed you may need to  blow it away and re-do your partitions then re-install. Would suggest the following:
  1. EFI
2. OS X
3. ext3 for ubuntu ("/" only, 8-12 Gb)
4. extended partition 
    - ubuntu "/home" (separate partition for this is sometimes pretty handy)
    - FAT32 "share" partitition
    - linux swap

   you will probably only need swap if you intend to use "suspend/hibernate", in which case 1.5 x <your amount of RAM> is recommended.
   I think the installer may make a swap no matter what but, if so, you can specify a much smaller amount.

2.  works nicely for me dual booting with xp

3. have not tried this, hopefully someone who has tried will have an answer for you shortly.

---

### Post by pxwpxw on 2007-10-07
> **jimrz said:**
> 1.  yes only 4 partitions, but 1 of them can be an "extended partition" which can contain numerous other partitions. Have you already installed ubuntu or just set up your partition table? If already installed you may need to  blow it away and re-do your partitions then re-install. Would suggest the following:
  1. EFI
2. OS X
3. ext3 for ubuntu ("/" only, 8-12 Gb)
4. extended partition 
    - ubuntu "/home" (separate partition for this is sometimes pretty handy)
    - FAT32 "share" partitition
    - linux swap

   you will probably only need swap if you intend to use "suspend/hibernate", in which case 1.5 x <your amount of RAM> is recommended.
   I think the installer may make a swap no matter what but, if so, you can specify a much smaller amount.

2.  works nicely for me dual booting with xp

3. have not tried this, hopefully someone who has tried will have an answer for you shortly.


Have you actually used that partitioning with the extended and logical MBR partitions,?
is that an Apple GPT/MBR compatible system?

I have not seen that before, but thought it might be possible.

---

### Post by cyberdork33 on 2007-10-08
If you plan to keep the GUID partitioning scheme (Apple default) then you cannot have extended or logical partitions. However, the opening poster is a bit confused. You can have more than 4 partitions. Ubuntu and OSX can both read many many partitions beyond #4. The issue is booting a legacy OS from one of them (and windows can only see the first 4 partitions).

As long as the Ubuntu partition that you boot from is one of the first 4, any of your other partitions can go wherever you want (I would leave the EFI partition in place though).

---

