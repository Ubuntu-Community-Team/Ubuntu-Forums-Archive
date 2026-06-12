---
title: "Install help"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by DUDE_2000 on 2007-05-11
I'd like to install ubuntu on a sony vaio, but there are two  things i need to do first
1. Wipe my **partitioned** drive
2.format them to fat32 
And afterwards i would like internet, but i am not sure if it will work, as we have only used windows so far...

I have never used linux, and neither has my dad


**Resolved**

---

### Post by DUDE_2000 on 2007-05-11
note: how do i do this, I will be grateful for any help
Thanks in adv.

---

### Post by starcraft.man on 2007-05-11
> **DUDE_2000 said:**
> I'd like to install ubuntu on a sony vaio, but there are two  things i need to do first
1. Wipe my **partitioned** drive
2.format them to fat32 
And afterwards i would like internet, but i am not sure if it will work, as we have only used windows so far...

I have never used linux, and neither has my dad

I'm not sure I understand exactly what you want, can you be a bit more clear... By "wipe" do you mean you want means of erasing all your data securely? Or just a cursory deletion to repartition? And what do you mean by format to fat32? If your moving entirely to Ubuntu then you would want Ext3 partitions for data. Unless you want a dual boot?

Can you be a bit clearer in your request, then I'll give you steps for install and setup.

Also, do you have an ATI or Nvidia card?

---

### Post by dstew on 2007-05-11
Hi DUDE_2000. Do you have Windows on your Vaio at present? If so, do you really want to completely delete it? You can have both Windows and Ubuntu (a dual-boot system) if you want to. It is no harder than wiping the whole disk and installing Ubuntu only.

---

### Post by drowner on 2007-05-11
I will repeat what starcraft said, and also i would like to point out then when i installed ubuntu my dad hadn't used linux either. :D

---

### Post by DUDE_2000 on 2007-05-11
i would like to get rid of all the data on my hdd
yes i am going to switch to linux, no dual boot

perhaps the word "reformat"  would of been better used

i have a nvidia card

---

### Post by DUDE_2000 on 2007-05-11
oh. yes i do have windows xp running but in a crippled state ( slow, no internet )

---

### Post by dstew on 2007-05-11
Why do you want to format the drive as FAT32? Linux will work better if you use its native format, ext3.

---

### Post by DUDE_2000 on 2007-05-11
> **dstew said:**
> Why do you want to format the drive as FAT32? Linux will work better if you use its native format, ext3.
sorry, Ive been told that linux has had trouble writing to ntfs, and i've read a blog 
 ( [http://consumer.hardocp.com/article.html?art=MTI5OCwxLCxoY29uc3VtZXI=](http://consumer.hardocp.com/article.html?art=MTI5OCwxLCxoY29uc3VtZXI=) )
where a guy switched to linux for 30 days and I read he used fat32

---

### Post by st33med on 2007-05-11
FAT32 is sorta a mess, even compared to ntfs standards (and those are low standards, believe me!). ext3 is better because it journalizes files, meaning it doesn't have to be defragged. Less time wasted, more speed.:popcorn:

---

### Post by starcraft.man on 2007-05-11
> **DUDE_2000 said:**
> i would like to get rid of all the data on my hdd
yes i am going to switch to linux, no dual boot

perhaps the word "reformat"  would of been better used

i have a nvidia card

Ok then, that makes my post very easy to write since your neither ATI nor wanting a dual boot.

Go here [first,]("http://www.ubuntu.com/getubuntu/download") and download the live CD of Ubuntu for your architecture (likely x86 the default). Then, you will have an iso on your drive. You need to burn it as a simple data disk(the iso contains the bootable files already) with any given burner (infra recorder is a free one if ya need it). Burn at a low speed to prevent errors.

Then pop the CD into your drive and follow the prompts to install. Read through [this]("http://www.psychocats.net/ubuntu/installing") page to see and understand every screen so you know what to do at every step.

For partitioning since you are moving to Ubuntu permanently, I recommend this partition scheme. All you need do to delete your previous data is select the partition and push delete in the partitioner.

Root Directory:
Mount to: /
Type: Primary
Format: Ext3
Size: 8 GB

Swap-File:
Mount to: swap-file
Type: Logical
Format: swap-file
Size: 2 GB

Home Folder: (your data will be stored here, seperate from OS and Apps)
Mount to: /home
Type: Logical
Format: Ext3
Size: X (where X is remainder of your drive)

I give you fair warning, Ubuntu is very different from windows.  You should try it first in the live CD to make sure its not too much of a culture shock :)

After you get it installed, please read the Ubuntu guide in my sig, it will help you get set up with programs you need. Thats about it, if you reconsider after trying live CD then want a dual boot, just leave your windows partition in tact at the partitioner and install root and swap (plus any extra to home) and Ubuntu will set up a dual boot for you when it installs grub.

Have fun with Ubuntu. :D

Edit: just read your posts, don't use fat32, if your switching entirely to Ubuntu that will be a bad choice, Ext3 is the format for data in Ubuntu.

---

### Post by DUDE_2000 on 2007-05-11
huh, I didn't know that
thanks

---

### Post by starcraft.man on 2007-05-11
> **DUDE_2000 said:**
> huh, I didn't know that
thanks

No problem, if you have any trouble installing just post back, but I feel confident the links and my suggestions should be enough. Hope to see you around the forums :)

---

### Post by DUDE_2000 on 2007-05-11
don't worry , I have a good working windows computer so i dont need my other one so much

---

### Post by DUDE_2000 on 2007-05-11
Thank you everybody!!
Everything you've provided me with will help alot!!!
at the moment I'm clearing the drives

---

### Post by starcraft.man on 2007-05-11
> **DUDE_2000 said:**
> Thank you everybody!!
Everything you've provided me with will help alot!!!
at the moment I'm clearing the drives

Your welcome, btw, if you ever want to make a complete secure wipe of your drives (say cuz your throwing em away or want to donate old comp to charity) use [DBAN]("http://dban.sourceforge.net/") for the wipe. ALL data will be irrecoverable (even by government :p)

---

### Post by DUDE_2000 on 2007-05-11
I downloaded the .iso, burned it strait onto a disk, put in the drive and....................................



windows opened up an explorer saying " ubuntu-7.04-desktop-i386.iso is on the disc ", no boot
do i have to expand the iso first, or wipe the os?

---

### Post by DUDE_2000 on 2007-05-12
never mind

---

### Post by starcraft.man on 2007-05-12
> **DUDE_2000 said:**
> never mind

All installed now I take it? If so, good to have you aboard the Ubuntu band waggon :D

---

