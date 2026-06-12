---
title: "I have the .iso, what's next?"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by adamdavid on 2006-07-07
Okay, I just downloaded the ubuntu-6.06-desktop-i386.iso file, in hopes that I will soon be running my first linux distro. Relying on tuts the whole way, I have become VERY confused with what to do in creating a bootable CD with Ubuntu.

I even tried running the start.exe file out of winRAR, but that just brought me straight to a browser with some links to install various applications.

Can any of you Linux-Gods please tell me where I could find some more information, or even provide some yourselves?

Thanks in advance.
Adamdavid.
(Yes, Adamdavid is my real name).

---

### Post by T700 on 2006-07-07
> **adamdavid said:**
> 

Can any of you Linux-Gods please tell me where I could find some more information, or even provide some yourselves?

Thanks in advance.
Adamdavid.
(Yes, Adamdavid is my real name).

Google is a great place to start.  "burn iso" will bring you quite a few, detailed results.  Basically, you use a CD/DVD creation program (Nero, for example) and tell it to burn the ISO.  Make sure you use the ISO setting.  Next, double check that your computer is set to boot from a CD.  If not, go into the BIOS and change it.  Put the CD in and reboot and follow the prompts.

You might also read _[this]("http://www.ubuntuforums.org/showthread.php?t=63315")_.

I'm not a Linux-God, nor any other kind of magical being, but like most people here, I'm happy to help you.

Paul

---

### Post by Jagot on 2006-07-07
[http://psychocats.net/ubuntu/iso.html](http://psychocats.net/ubuntu/iso.html)
[http://psychocats.net/ubuntu/installing.html](http://psychocats.net/ubuntu/installing.html)

---

### Post by FredB on 2006-07-07
Linux-gods ?

Wow. Isn't this a little too big ? ;)

---

### Post by adamdavid on 2006-07-07
I'm all set, except for booting from the CD, which is proving to be quite difficult.

I'm running PhoenixBIOS, and I'm lost
Thanks in advance again, Linux Gods!

---

### Post by Frank Golden on 2006-07-07
> **adamdavid said:**
> I'm all set, except for booting from the CD, which is proving to be quite difficult.

I'm running PhoenixBIOS, and I'm lost
Thanks in advance again, Linux Gods!
LOL, Linux Gods! I,m an old atheist. LOL
Can you get into bios? If so there should be an option to place
your CD drive #1 in boot order. I'm using Phoenix also on 
an Acer laptop but yours could be slightly different.
Once you change boot order your computer should boot to CD.
If you used Nero to make CD you should use burn image option in
the recorder menu. Start Nero burning rom and cancel the new
compilation wizard. Then choose "burn image" from recorder menu.
Point to image and burn. This will make a bootable CD.
If you don't have Nero M$ has a tool available to burn iso images.
[http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm) 
It's free and works great. When installed just right click iso
and choose burn image with isorecorder option.
Linux Gods!:lol:

---

### Post by adamdavid on 2006-07-07
I am typing this message in UBUNTU!

---

### Post by T700 on 2006-07-07
> **adamdavid said:**
> I am typing this message in UBUNTU!

Congrats!  

Paul

---

### Post by hellmet on 2006-07-07
hmm..well congrats..
so how do u feel with ur very first linux experience??

---

### Post by adamdavid on 2006-07-07
Well, it isn't too bad. It will take some getting used to. But, I will not be a full time user. I may want do a project on Ubuntu for school or something.

Honestly, this was just a learning experience. Thanks to all who helped.

---

### Post by adamdavid on 2006-07-07
One more quick question. Will I be able to install programs, such as, VIM? If so, will they go onto the CD rom that I am running on, or my HD?

Thanks, Adamdavid.
(yes, that is my real name.)

---

### Post by crystal on 2006-07-07
Vim is probably already installed. To check, try:
vi --version

---

### Post by FredB on 2006-07-07
With a standard dapper install :

vi --version : VIM - Vi IMproved 6.4 (2005 Oct 15, compiled May 23 2006 12:03:57)

/me thinks about grabbing / installing VIM 7.0 ;)

---

### Post by Frank Golden on 2006-07-07
If you have some extra space on your HD you might want to consider dual booting. [http://users.bigpond.net.au/hermanzone/index.htm](http://users.bigpond.net.au/hermanzone/index.htm)

The above was written for the Alternate CD which you can download
from the same place you got the Desktop CD from.

Give it a read, good info.

If you do back up your data of course.

---

### Post by adamdavid on 2006-07-07
You might not have understood the question, sorry.
I'll try to explain again.

Since I don't have Ubuntu installed, it's just on a live disc, am I still able to install Linux programs? I mean, differient programs that did not come with Ubuntu.

If so, will they be stored on my HD, or the CD that Ubuntu is running from?

Thanks!
Adamdavid.

---

### Post by T700 on 2006-07-07
> **adamdavid said:**
> You might not have understood the question, sorry.
I'll try to explain again.

Since I don't have Ubuntu installed, it's just on a live disc, am I still able to install Linux programs? I mean, differient programs that did not come with Ubuntu.

If so, will they be stored on my HD, or the CD that Ubuntu is running from?

Thanks!
Adamdavid.

Neither.  They will exist only in RAM.  As soon as you shut down, they go away.  Due to the limited amount of RAM, you will not be able to install a great deal of things.

Paul

---

### Post by adamdavid on 2006-07-07
Thanks so far, but I have one more question. (Maybe :) )
So, due to some computer problems in the past,  I chose to re format my HD. While reformating, I partitioned the HD into 2 equal parts. (One for my brother, and one for me.)

If I wanted to dual boot Windows XP and Ubuntu, could I install Ubuntu to my HD, using the "wipe my drive option" or would I have to partition my already partitioned hard drive?

Sorry if that was unclear.
Thanks in advance.
Adamdavid.
(Yes, that is my real name)

---

### Post by -deadcats on 2006-07-07
Assuming you want to keep XP, which tends to be installed on the first partition, you can either "wipe" the second partition and install Ubuntu there, or resize the second partition and create a new one in which to install Ubuntu and one for the swap file. Ubuntu will make some suggestions, but you don't necessarily want to use them. You may want to  "manually" partition your HDD, something I would suggest for an experienced user. So how experienced are you? You know enough to have partitioned your HDD before, so that means you understand something about disc layout, what partitioning is and does. You've got the basics, but you will need to learn  Linux and GRUB disc nomenclature so we can communicate. You can find that here somewhere I'm sure. I'd suggest a forum SEARCH.

Considering you're wanting to do something more complex than installing to a bare, no-OS drive, there are a variety of options and planning (like where and how large of a swap partition) that need to be considered. Sone of the questions you need to ask yourself are how important is my data, how important my brother's stuff, and how much room do I have?

I tend to make these kinda suggestions then vanish once again into hyperspace. But I'm sure if that if you have any more questions, someone else will be along in a little bit to help you.

regards,
-dc

---

### Post by Frank Golden on 2006-07-07
> **adamdavid said:**
> Thanks so far, but I have one more question. (Maybe :) )
So, due to some computer problems in the past,  I chose to re format my HD. While reformating, I partitioned the HD into 2 equal parts. (One for my brother, and one for me.)

If I wanted to dual boot Windows XP and Ubuntu, could I install Ubuntu to my HD, using the "wipe my drive option" or would I have to partition my already partitioned hard drive?

Sorry if that was unclear.
Thanks in advance.
Adamdavid.
(Yes, that is my real name)
Your second partition is it empty? If it is use Windows
Admin tool diskmgt.msc to delete it. Then choose the option in the Ubuntu routine to install to the largest free space
automatically. Ubuntu will do the rest. You may get a prompt to install GRandUnifiedBootloader (GRUB) for short. Allow. After you install and reboot you will be presented with GRUB menu if you do nothing Ubuntu will boot in ten seconds. Or you can use arrow keys to scroll down to XP and boot XP. You can edit 
/boot/grub/menu.lst to place XP as first choice if needed.
See the tutorial I linked to earlier for info about GRUB.
Give it a shot you may be pleasantly surprised. Great learning
experience. Again remember to back up and read the section about removing Ubuntu
in case you want to remove, it's not difficult but you do have a procedure to follow. Good Luck.

P.S. Ubuntu will create an ext3 partition on the free space (unallocated space)
and an appropriately sized ext2 swap partition, all automagically.
If you are adventurous use the tutorial and download the Alternate CD the tut was written for. Again part of the learning curve. Ask questions, make use of google and these forums and you can't help but have success.

---

