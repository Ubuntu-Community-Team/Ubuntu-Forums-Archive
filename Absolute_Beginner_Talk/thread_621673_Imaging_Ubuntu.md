---
title: "Imaging Ubuntu"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-11-23
Ubuntu's Great but I would like the piece of mind I have with Ghost on Windows.
It's nice knowing if anything ever messes up that I can just put in my DVD Image
I've made and be back to normal in 15 minutes.  Is there a Program for Ubuntu
that will make a Bootable full system Image like Ghost....

Thanks......

---

### Post by lazyart on 2007-11-23
Get the Clonezilla/Gparted cd.  It's what I use for imaging.

---

### Post by Mithrilhall on 2007-11-24
I've used Acronis in the past and it worked perfectly for me.

---

### Post by Orbital75 on 2007-11-24
Thanks...... Do these offer Bootable DVD options?
If so, looks like what I'm looking for.

---

### Post by Phurious on 2007-11-24
I still use Ghost.  I boot from a USB drive and capture an image of my Ubuntu drive with no issues.

---

### Post by k3lt01 on 2007-11-24
> **Phurious said:**
> I still use Ghost.  I boot from a USB drive and capture an image of my Ubuntu drive with no issues.Would you be able to write up a "How to" on using Ghost to do this? I have the latest Ghost which I purchased for Ghosting my laptop's XP setup and my Desktop's Vista setup.

If I could Ghost Ubuntu I would be alot happier about upgrades, especially since the upgrade to Gutsy and subsequent reinstall of Feisty afterwards lost me so much setup time.

---

### Post by Phurious on 2007-11-24
The USB drive is imaged with Windows PE 2.0 - the latest "Vista" version of Windows PE.  I chose to use it because it offers a lot of new enhancements over the older versions of PE (Including BartPE) such as USB plug and play and a MUCH easier process for driver installation.  I am using Symantec Ghost v11.0 on the PE image.  I have tried earlier versions of Ghost, but had problems due to the EXT3 FS; version 11 has not failed me.  I have not tried version 12.  the question is does it have a separate GHOST32.EXE that can be run by itself?

The process is actually pretty straight forward; the caveat is you require access to a Windows XP or Vista machine (Perhaps one in VMWare might work, I have never tried) and a copy of the Windows Vista WAIK from Microsoft.  The WAIK is free for download from MS, and is 900+ MB so D/L may take a bit depending on your pipe.

Download and install the Vista WAIK (Windows Advanced Installation Kit)
Build your image.  There is a CHM in the docs folder when you install the WAIK that provides good documentation and several walk-throughs, including one to boot from USB.

Copy any tools you need (GHOST32.EXE) to the bootable USB drive and viola!

---

### Post by dips_xe on 2007-11-24
[ghost 4 linuxl]("http://sourceforge.net/projects/g4l").

i don't know how well this works or if it is fully developed, look into it

---

### Post by k3lt01 on 2007-11-24
Thanks Phurious

---

### Post by Orbital75 on 2007-11-24
That sound like something I'd like to do but seems to be over my head a little.
I'd like to set that all up but don't know how.  What's Windows PE?

---

### Post by Phurious on 2007-11-24
> **Orbital75 said:**
> That sound like something I'd like to do but seems to be over my head a little.
I'd like to set that all up but don't know how.  What's Windows PE?

Windows PE stands for "Windows Pre-Installation Environment".  It is essentially a watered-down version of Windows that Microsoft used to provide to "Partner" companies or VERY large enterprise sized companies to aid in the deployment of Windows.  It provide more functionality than a DOS boot disk, but much less than a full-fledged Windows install.  With the release of version 2.0 it is also now fairly customizable.

[http://en.wikipedia.org/wiki/Windows_PE]("http://en.wikipedia.org/wiki/Windows_PE")
[http://technet.microsoft.com/en-us/windowsvista/aa905120.aspx]("http://technet.microsoft.com/en-us/windowsvista/aa905120.aspx")

---

### Post by Bigbird999 on 2007-11-24
If you are dual booting you already have everything you need.   You can use Ghost - Acronis - etc to make an image of your linux partition.  I have a Windows partition, Ubuntu partitions (OS + swap) and a Fat32 partition that windows and Ubuntu share.  I store an image of both Windoze and Ubuntu on the shared  partition.  If I want to revert to an imaged version of ubuntu I boot into windows and run Acronis to restore the Ubuntu partition.  If my windows craps out, I can use my Acronis boot disk to restore the windows partition  

I know it is not a "pure Linux' solution but it works and is easy, if you are used to windows.

BB

---

### Post by Orbital75 on 2007-11-24
Do you think that It could be preformed through USB?
Windows is on my Primary internal Drive while Linux boots
via a USB External Enclosure.

---

### Post by gn2 on 2007-11-24
Here's another option: [http://ubuntu-unleashed.blogspot.com/2007/09/remaster-and-clone-your-ubuntu-install.html](http://ubuntu-unleashed.blogspot.com/2007/09/remaster-and-clone-your-ubuntu-install.html)

---

### Post by Daveski on 2007-11-24
> **lazyart said:**
> Get the Clonezilla/Gparted cd.

+1 from me. This is basically a non-GUI, but multiple choice (with good tips) 'wizard'. It is very handy to have a decent understanding of Linux notations for drives and partitions before you run this otherwise it might be a bit scary first time round.

Ghost and Drive Image can work quite well with Linux systems but need licenses ;-(

---

### Post by Orbital75 on 2007-11-25
> **gn2 said:**
> Here's another option: [http://ubuntu-unleashed.blogspot.com/2007/09/remaster-and-clone-your-ubuntu-install.html](http://ubuntu-unleashed.blogspot.com/2007/09/remaster-and-clone-your-ubuntu-install.html)

Thats interesting..... So, it makes your current Setup into a Installable LiveCD.

---

### Post by gn2 on 2007-11-25
> **Orbital75 said:**
> Thats interesting..... So, it makes your current Setup into a Installable LiveCD.

Or LiveDVD depending on size.

---

### Post by gilf on 2008-01-17
I use partimage. 

Particularly handy when found on the Parted Magic CD. This CD is only about a 30 megabyte download, but you get al GUI Linux LiveCD desktop with all kinds of partition, burning, and imaging tools pre-installed.

[www.partedmagic.com/](www.partedmagic.com/)

At 30 Mb It's a doable  download even with a dialup connection. I did it overnight. This disk will do a lot more than Ghost will, and it's free instead of $70.

I've used it not only to back up partition images, but make VMWare virtual machines, resize virtual machines, back up basically anything. It's a great tool -- looks good, too.

---

### Post by kimangroo on 2008-01-21
^ +1 for Partimage

I just finished backing my very small Ubuntu partition and it took 5min for the 2.5 GB or so. Haven't restored yet though so can't comment on that.

I used the [_system restore cd_]("http://www.sysresccd.org/Main_Page") mentioned on lifehacker. They've got a little tute on it [_here_]("http://lifehacker.com/software/geek-to-live/partition-and-image-your-hard-drive-with-the-system-rescue-cd-292972.php").

---

