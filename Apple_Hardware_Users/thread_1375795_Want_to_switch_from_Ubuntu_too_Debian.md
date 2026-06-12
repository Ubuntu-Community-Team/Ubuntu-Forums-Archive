---
title: "Want to switch from Ubuntu too Debian"
date: 2010-01-08
forum: Apple Hardware Users
---

### Post by Chris Grk-O-Matic on 2010-01-08
1ghz Titanium PowerBook, 1gig RAM

3 Partitions:
Ubuntu - 4.7 gigs - Mac OS Extended format 
   OS 9 - 1.1 gigis - Mac OS Extended format 
   OS X - 87 gigs - Mac OS Extended format 

I may want to switch to Debian but leave OS9 & X unscathed. Can someone give me a detailed approach to doing this, i.e, setting mount points, partition scheme? I really don't want to mess anything up as I'm somewhat bewildered with all the different schemes.


Regards,
Chris

---

### Post by linuxopjemac on 2010-01-08
here you find a goodd tutorial by our friend Oswald Kelsoo
[http://forums.debian.net/viewtopic.php?f=16&t=20481](http://forums.debian.net/viewtopic.php?f=16&t=20481)

---

### Post by Chris Grk-O-Matic on 2010-01-08
It is a nice tutorial but I'm afraid it doesn't help my situation as it says to use guided partitioning - which I don't want to do because I want to keep my partitions with OS9 and OSX.

---

### Post by linuxopjemac on 2010-01-08
If you go for advanced, you can set the root to the one you have ubuntu on. I would amend the bootloader settings manually after debian is installed from a tty console. Don't forget to ybin.

---

### Post by linuxopjemac on 2010-01-08
is it true that you have ubuntu running now or not ? I am a little confused by the fact that your Ubuntu partition is MacOS extended.

---

### Post by Chris Grk-O-Matic on 2010-01-08
That's a typo, sorry for the confusion. The partition with Ubuntu is just HFS.

Can you perhaps elaborate a little more on your installation suggestion?

---

### Post by linuxopjemac on 2010-01-09
First of all, I would make a backup of your complete system. I can recommend to download and burn CloneZilla. It can simply clone the complete hard disk in the state it's in right now. If things fail, you should be able to put things back as it was before you started with Linux.

The linux part. I can recommend Debian Lenny. It is easier to install than Ubuntu to my humble opinion. Download the [netinstaller]("http://cdimage.debian.org/debian-cd/5.0.3/powerpc/iso-cd/debian-503-powerpc-netinst.iso"). md5 it to be sure that it is the right iso. Burn it to a CD at low speed. Then start your Mac from the CD by holding the "C" key pressed. I would go for an advanced setup. I don't really remember what options you have. But from the partitioner I would just erase the Ubuntu partition and create a small bootloader partition in HFS (200 Mb) and a swap partition equally big as your RAM (ext3). The rest I would use as / (root) (also in ext3) and set a boot flag on this one. Then let the installer do its job. At the end, I don't really remember because it's a while ago that I installed Lenny on my Pismo, you have to install the bootloader manually on the 200 Mb partition. Hopefully with this info you can get going. Let us know how it goes...

On my own website (mac.linux.be) you will find a lot of information on how to install Linux on PPC machines, like yours. I can recommend it to read a bit before you really go for it.

---

### Post by Chris Grk-O-Matic on 2010-03-04
Sorry wrong catagory.

---

### Post by oswaldkelso on 2010-03-05
> **Chris Grk-O-Matic said:**
> It is a nice tutorial but I'm afraid it doesn't help my situation as it says to use guided partitioning - which I don't want to do because I want to keep my partitions with OS9 and OSX.


Then choose manual.   :)

Choice is good..... unless you chose Windows, OSX, BSD, or any other thing I'm not into :D

Choice is good  If you chose GPL.2+..AGPL... Debian main.. kernel-libre  etc..  

Newbies read up ;) knowledge is power...

---

