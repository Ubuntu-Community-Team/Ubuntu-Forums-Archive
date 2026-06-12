---
title: "[SOLVED] Newbie wants to get to grips with ubuntu"
date: 2008-05-05
forum: Apple Hardware Users
---

### Post by hnlntm on 2008-05-05
Hi all,

I can use a PC and MAC with ease (MAC being the prefered platform). I want to use Ubuntu as an alternative to windows. 

I've played with ubuntu nearly a year ago and couldn't quiet get the hand of it but I want to give it a try again. I want to use the desktop version but not sure if I need to choose amd64 intel computer or if I need the standard desktop? I will also be using this via bootcamp.  my computer specs are:

24-inch iMac - Leopard 10.5.2 
2.16GHz Intel Core 2 Duo
4MB Shared
1GB (2x512MB) 667MHz DDR2 SDRAM (PC2-5300), supports up to 3GB
250GB Serial ATA 7200 rpm
Slot-loading 8x SuperDrive with 2.4x Dual Layer burn (DVD+R DL/DVD±RW/CD-RW)
24-inch (viewable) widescreen TFT active-matrix LCD, 1920 x 1200 pixels, millions of colors
Built-in iSight; Mini-DVI output port with support for DVI, VGA, S-video, and composite video connections via adapter 
NVIDIA GeForce 7300GT with 128MB GDDR3 SDRAM
One FireWire 400 and one FireWire 800 port; 15 watts shared
Built-in stereo speakers, built-in microphone, optical digital audio output/headphone out, optical digital audio input/audio line in
uilt-in 54 Mbps AirPort Extreme (802.11g)3; built-in Bluetooth 2.0+EDR (Enhanced Data Rate) module.
Built-in IR Receiver, optional VESA mount adapter kit

Thanks all in advance :confused:

---

### Post by tamoneya on 2008-05-05
just use the i386 (32 bit) version.  You could use the 64 bit version although it most of the time just causes problems with things like flash.

---

### Post by hnlntm on 2008-05-05
Thanks tamoneya I've downloaded the latter, with your advice I might play with both versions, any idea if theres any real difference in overall performance?

---

### Post by tamoneya on 2008-05-05
there is a performance difference but for most applications and most users it isnt noticable.  The reason why most people use 64 bit instead of 32 bit isnt the performance difference but that 64 bit can handle more than 4GB of RAM while 32 bit cant.  There are a million threads on the forums that go into the details of 64 bit vs 32 bit if you are interested in learning more.

---

### Post by hnlntm on 2008-05-05
Thanks again, I think I'll stick with the 32bit version.

a :KS for you:)

---

### Post by Webdemic on 2008-05-06
If you are installing Ubuntu on Mac hardware, I highly suggest using Refit (it is Mac software). It is a free program that presents a nice little menu of installed OSs when you boot, and allows you to update the MBR. I've had terrible luck installing Hardy on my macbook without it (not sure why). 

Another thing to keep in mind is that if you are planning on installing that "other" operating system, you will need to keep your number of partitions in check. If this is something you are considering, you will want to plan ahead. There are plenty of posts on triple booting, but the gist of is to keep Ubuntu on a single partition (ie you have to make a swap file instead of a whole partition).

Best of luck to you.

---

### Post by hnlntm on 2008-05-06
> **Webdemic said:**
> If you are installing Ubuntu on Mac hardware, I highly suggest using Refit (it is Mac software). It is a free program that presents a nice little menu of installed OSs when you boot, and allows you to update the MBR. I've had terrible luck installing Hardy on my macbook without it (not sure why). 

Another thing to keep in mind is that if you are planning on installing that "other" operating system, you will need to keep your number of partitions in check. If this is something you are considering, you will want to plan ahead. There are plenty of posts on triple booting, but the gist of is to keep Ubuntu on a single partition (ie you have to make a swap file instead of a whole partition).

Best of luck to you.
I have got windows xp runing on a partion via boot camp. Is it possible to add an additional partion for ubuntu without the need of formatting either my windows or mac partion.....and if there is can you point me the direction for a guide. Thanks

---

### Post by cyberdork33 on 2008-05-06
> **Webdemic said:**
> Another thing to keep in mind is that if you are planning on installing that "other" operating system, you will need to keep your number of partitions in check. If this is something you are considering, you will want to plan ahead. There are plenty of posts on triple booting, but the gist of is to keep Ubuntu on a single partition (ie you have to make a swap file instead of a whole partition).
Windows does not limit you to four partitions, it is just limited to seeing the first four partitions. In other words, any partition that you want to access from Windows needs to be one of the first four. a swap partition would never need to be accessed from windows so put it wherever you want.

---

### Post by Webdemic on 2008-05-06
You should be able to resize your NTFS partition with GParted. Just remember, backup everything. Resizing partitions can lead to data loss.

You'll need an Ubuntu liveCD. GParted should appear under "System->Administration" once you have logged in.

Here is some more information for you to look over. I hope this helps:

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

### Post by cyberdork33 on 2008-05-06
> **Webdemic said:**
> GParted should appear under "System->Administration" once you have logged in.and it is called "partition editor"

---

### Post by Webdemic on 2008-05-07
It might be worth checking out Wubi ([http://wubi-installer.org](http://wubi-installer.org)). You could (in theory) install Ubuntu on your Windows partition, saving you from having to repartition your hard-drive. It is definitely worth looking into, but I can't say I know much about it.

---

### Post by avtolle on 2008-05-07
I've used Wubi to install HH on an AMD-64 laptop, and have had no problems with it. I do see from the Wubi forum there are many who have had and have problems. FWIW, should you try this route, download the installer under windows from the link Webdemic posted, and let it d/l the iso. Seems to work better (that's how I did it). Good luck. BTW, as I note that the OP has d/l both the 32 bit and 64 bit isos, consultation should be had to the FAQs at the Wubi site on how to install from a previously downloaded iso. If one allows the Wubi installer to do it all, then the AMD-64 version will be d/l and installed.

---

