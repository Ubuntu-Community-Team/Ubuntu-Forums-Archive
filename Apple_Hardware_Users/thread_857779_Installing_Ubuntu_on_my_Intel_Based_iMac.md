---
title: "Installing Ubuntu on my Intel Based iMac"
date: 2008-07-12
forum: Apple Hardware Users
---

### Post by Vuluptous Vortexouses on 2008-07-12
Please help, I've done everything I can.

I've followed all the given instructions, yet still I can not seem to get this to work. 

Can someone please explain to me how exactly I can install Ubuntu on my computer?

I have downloaded it, burned in onto a disc. Nothing happens other than a a disk image with lots of folders in it.

Clearly, I have no idea what I'm doing.

Any help would be much appreciated.

---

### Post by ad_267 on 2008-07-12
Ok so you have the disc burnt properly but you don't know how to boot from it?

You need to restart your computer with the cd in the drive and get your computer to boot from the cd. I have no experience with macs but after searching for "imac boot from cd" it looks like you have to hold down the c key when you turn on your computer.

---

### Post by cyberdork33 on 2008-07-12
yep. If you are running into problems elsewhere, please be more specific with exactly where you run into trouble. You can also try holding Option on startup to get a boot menu. Also, if you install rEFIt first, it will always show the bootable CD as an option.

---

### Post by Vuluptous Vortexouses on 2008-07-12
Thank you very much. 

I'll be sure to try this and will provide feedback.

---

### Post by Oscar Pradilla on 2008-07-13
Well i've done that..you wont be sorry...but i most warn you....once you've tried...probably you'll neve go back to mac os.  

1. You need to identify your mac to download the right ubuntu:
a. Intel core duo: Download the x86 cd image
b. Intel core duo 2: Download the 64 cd image (better performance)

2. Decide: dual boot or single boot (ubuntu) if you are tinking on switching..well try first dual boot if you like it, go for it..
3. Sigle boot (Ubuntu): start mac, put cd, press C and wait (Before the apple appears, if it's already on the screen, turn off and try again), the installer will appear, then use automatic partition and it will do the rest... (Remember to save your files, time machine file structure isn't a good backup for this, better copy everything...)

4.Dual boot then: start and log into mac os, then run boot camp assistant, choose size of partitión 40 GB will do the work, and apply,  then select quit and install later when it finish.  
5. Put the ubuntu cd in the drive, and restart
6. once again press C until installer appear, then choose install ubuntu
7. On the partition process choose manual, then the new partition destined for windows (boot camp)  has a FAT format, select that and press delete partition, the partition software will now show you a free space of 40GB, select that and choose new partition
8. Make it 1GB smaller (so 39GB), file system: EXT3 , Mounting point: /   apply
9. With the 1GB: new partition, file system: Swap   apply
10. Next...next...next...the rest is almost automatic

After everything has finished..

11. To start with ubuntu:  Start mac, press Alt until the start options appear, select windows (this contains the ubuntu installation, the name was given by boot camp) and press enter 
12. Also you can try install rEFit [http://refit.sourceforge.net/]("http://refit.sourceforge.net/")
it will create a boot menu.

13. So, take the Red pill and feel free to try, i've installed and unistalled mac os and ubuntu so many times before decide to stay with ubuntu...but is worting...

---

### Post by Vuluptous Vortexouses on 2008-07-13
I successfully got onto Ubuntu.

I gave it a test run (the option in which you don't install to see if it works) and it did indeed work but I still have two problems.

1. I can't connect to a wireless network! It does not even give me the option to do this.

2. To the post above me, I am already using Boot Camp to access Windows. Should Windows be deleted? Should I just use the provided software you linked?

Thank you everyone for your considerable amount of help.

---

### Post by DonnieP on 2008-07-13
> **Vuluptous Vortexouses said:**
> I successfully got onto Ubuntu.

I gave it a test run (the option in which you don't install to see if it works) and it did indeed work but I still have two problems.

1. I can't connect to a wireless network! It does not even give me the option to do this.

2. To the post above me, I am already using Boot Camp to access Windows. Should Windows be deleted? Should I just use the provided software you linked?

Thank you everyone for your considerable amount of help.

(1) What kind of Mac is this and (2) do you want to keep Windows?

---

### Post by Oscar Pradilla on 2008-07-13
I recomend you to save and post the mac configuration, the one you got at About this mac... it will  help you through the process...

This post [https://help.ubuntu.com/community/MacBookPro]("https://help.ubuntu.com/community/MacBookPro") will help you with triple boot and things like that..

Also and most important do not erase mac os partition until you got everything working...(you may need to save some files from mac os system as firmware for isight and wireless) after the system runs as you want, you're ready to go and make the full switch...


Go ahed...i almost quit, but there are a lot of nice people around who will help you to stay with ubuntu....

---

### Post by Vuluptous Vortexouses on 2008-07-13
> **DonnieP said:**
> (1) What kind of Mac is this and (2) do you want to keep Windows?

Hardware Overview:

  Model Name:	iMac
  Model Identifier:	iMac7,1
  Processor Name:	Intel Core 2 Duo
  Processor Speed:	2.4 GHz
  Number Of Processors:	1
  Total Number Of Cores:	2
  L2 Cache:	4 MB
  Memory:	2 GB
  Bus Speed:	800 MHz
  Boot ROM Version:	IM71.007A.B03
  SMC Version:	1.21f4


Yes, I want to keep windows, for now. I am simply only interested in "trying" Ubuntu for a few weeks.

Also, to clear any confusion I also want to keep the mac partition, however in the iMac installation guide on the documentation it tells me to delete the third partition. 

Thanks once again.

---

### Post by cyberdork33 on 2008-07-15
> **Vuluptous Vortexouses said:**
> Yes, I want to keep windows, for now. I am simply only interested in "trying" Ubuntu for a few weeks.

Also, to clear any confusion I also want to keep the mac partition, however in the iMac installation guide on the documentation it tells me to delete the third partition. 
That partition is not your Mac OS partition. Also those instruction are really just for dual booting. follow the MacBook Pro triple-boot guide.

For wireless, I would start a new thread and be more descriptive about the problem. What did you do? (ndiswrapper?)

---

