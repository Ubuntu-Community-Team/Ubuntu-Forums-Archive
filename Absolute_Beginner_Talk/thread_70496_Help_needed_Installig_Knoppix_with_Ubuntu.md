---
title: "Help needed: Installig Knoppix with Ubuntu"
date: 2005-09-30
forum: Absolute Beginner Talk
---

### Post by thtan on 2005-09-30
I had Ubuntu previously installed Ubuntu on my secondary HD, let's called it d:\ in windows term or hdb1 and hdb5(for the linux swap) in linux terms. I have winXP running on  my primary disk C:\ (hda1) with the help of GRUB (which was installed with Ubuntu).

I would like to install Knoppix on the same hard disk with Ubuntu. My question would then be: 

I had dedicated a whole hd (with only the ext3 partition) for my linux distros (with currently only Ubuntu running on it). Do i hav to do any kind of partion again to accomodate for the Knoppix file systems?

Does the installation of Knoppix affects/corrupt my boot sequences in GRUB? What boot loader does Knoppix uses? Will Knoppix recognize my current boot loader configurations?

Any comments/suggestions are welcomed. Thanks 4 d support!

---

### Post by mlomker on 2005-09-30
> Does the installation of Knoppix affects/corrupt my boot sequences in GRUB?

How were you planning to install Knoppix?  I've heard about people somehow copying the CD image to a disk and then getting the image to boot.  It isn't really intended to run from disk, though.

---

### Post by Kapre on 2005-09-30
[QUOTE=thtan]I had dedicated a whole hd (with only the ext3 partition) for my linux distros (with currently only Ubuntu running on it). Do i hav to do any kind of partion again to accomodate for the Knoppix file systems?[/QUOTE] I would say yes, you need to have a new partition for your knoppix. If you will not create a new partition it will overwrite your Ubuntu.

> Does the installation of Knoppix affects/corrupt my boot sequences in GRUB? What boot loader does Knoppix uses? Will Knoppix recognize my current boot loader configurations?
Any comments/suggestions are welcomed. Thanks 4 d support! I think Knoppix by default is using LILO as its bootloader and if you decide to use it, it will overwrite your GRUB.

K

---

### Post by thtan on 2005-10-01
mLomke, I intend to have Knoppix installed into my hd, instead of booting through an image file.

Kapre, what happens when LILO does overwrite my GRUB? Does LILO recognizes my other OS (WinXP and Ubuntu) and set them up properly? Can i use the partition manager that comes with Ubuntu installation CD to do the partition b4 i install Knoppix? Personally, I think it's possible, but juz would like to b sure.

---

### Post by mlomker on 2005-10-01
> mLomke, I intend to have Knoppix installed into my hd, instead of booting through an image file.

You can't do that, which is why I asked.  

I've heard of people copying the ISO file to a hard disk and then booting from it somehow, but you can't install it.

---

### Post by thtan on 2005-10-04
mLomke, I don't think ur advice is absolutely correct.
Basically, knoppix can be downloaded as an image file *.iso which can be run as an live cd, if u burn the image into a cd. When it boots up, u can type some sort of command like "kx hdinstall" to install the image on the hd if i'm not mistaken.

My point is, it is "indeed possible" to install knoppix onto a hd.

---

### Post by matthew on 2005-10-04
I'm quite sure it is possible to install Knoppix on a hard drive. It ends up being a slightly customized Debian. I seem to recall there was a howto for installing Knoppix to a hard drive somewhere on the Knoppix cd. Look in the documentation html pages.

---

### Post by UbuWu on 2005-10-04
[QUOTE=matthew]I'm quite sure it is possible to install Knoppix on a hard drive. It ends up being a slightly customized Debian. I seem to recall there was a howto for installing Knoppix to a hard drive somewhere on the Knoppix cd. Look in the documentation html pages.[/QUOTE]

[http://www.knoppix.net/wiki/Hd_Install_HowTo](http://www.knoppix.net/wiki/Hd_Install_HowTo)

---

### Post by mlomker on 2005-10-04
> My point is, it is "indeed possible" to install knoppix onto a hd.

Yes, I overstated the case and I had heard of people installing it.  I was just hoping you'd point me to a how-to, but someone else did that.  It looks like they are suggesting a convoluted combination of debian standard repos and apt-pinning. 

I can't imagine that box would stay usable for long...just a matter of time before a standard package overwrote a customized one and it'd stop working.  I ruined a Linspire box playing around with those kind of setups.

I personally run VMWare because you can boot a machine from ISO with it.

---

### Post by kawinter on 2005-10-05
[QUOTE=mlomker]Yes, I overstated the case and I had heard of people installing it.  I was just hoping you'd point me to a how-to, but someone else did that.  It looks like they are suggesting a convoluted combination of debian standard repos and apt-pinning. 

I can't imagine that box would stay usable for long...just a matter of time before a standard package overwrote a customized one and it'd stop working.  I ruined a Linspire box playing around with those kind of setups.

I personally run VMWare because you can boot a machine from ISO with it.[/QUOTE]

I installed Knoppix/Debian on my Dell Inspiron Laptop more than a year ago and have had no problems.  I did have a problem with a Knoppix desktop becoming unstable.  BUT here is a point I would like to make.  With Ubuntu there is no particular reason to install Knoppix.  All Knoppix does is give you a great initial install of a system that is basically Debian and the install includes a ton of apps.  When I installed Ubuntu on the home system all I had to do to match what Knoppix would have given me was do apt-get install on the apps I wanted.  Knoppix doesn't offer anything Ubuntu doesn't offer so why add it to an Ubuntu system?

---

### Post by mlomker on 2005-10-05
> Knoppix doesn't offer anything Ubuntu doesn't offer so why add it to an Ubuntu system?

I agree with you on that.  I keep a copy around because I think it's great as a disaster recovery CD (more useful software installed on it than Ubuntu's liveCD for example), but I don't see a point to installing it.

---

### Post by thtan on 2005-10-06
Ya, i see your points there, and i do agree with them. Knoppix is really good to act as arecovery disk while ubuntu can stay on my hd. 

Mayb my real concern was getting a particular program to be installed onto my ubuntu. It's called network simulator 2 and i was trying to build it from source ([http://www.isi.edu/nsnam/dist/ns-allinone-2.28.tar.gz)](http://www.isi.edu/nsnam/dist/ns-allinone-2.28.tar.gz)). 

I tried to install it but failed several times, saying that tk83d (one of the header files in package tk83 was in error). Found a distro called Zourix which runs using Knoppix, so i guessed i ould juz used it instead.

Ya, mayb my next question should b how to  install ns2 on ubuntu?
Any comments?

---

### Post by mlomker on 2005-10-06
Hoary has tk8.4 installed.  Did try installing tk8.4-dev?

---

