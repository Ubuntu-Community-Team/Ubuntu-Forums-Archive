---
title: "No Operating System"
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by Zunkie on 2006-04-19
How do you install Ubuntu when you don't have an operating system to read the CD with ubuntu??????? Any help would be greatly appreciated.  Thank you!

---

### Post by sYs^ on 2006-04-19
Ubuntu CD boot by itself on system start, just set CD-ROM for your 1st boot device in your BIOS.

---

### Post by nalmeth on 2006-04-19
Do you have an Ubuntu CD?
If so you don't need any operating system.
When you start your computer, enter your BIOS settings, usually either by hitting DELETE or F10 or whatever you are prompted to enter.
Find the boot order, and make sure you can boot from the CD. That's it.

---

### Post by Zunkie on 2006-04-19
CD-ROM is set as the first in my BIOS setting.  I did download a Ubuntu CD but I'm not sure if it eve works.  I tried to open it from my windows based desktop (I want to put Ubuntu in my laptop) but it wouldnt open it there either.  So I am really unsure what to do
Any help is great! Thank you all in advanced

---

### Post by aysiu on 2006-04-19
An .ISO doesn't open. It's a disk image, not a collection of files.

---

### Post by stoeptegel on 2006-04-19
You have to burn the image as disc/cd/dvd image first, then get the boot order correct so it boots of your cd.

---

### Post by Nrbelex on 2006-04-19
Did you burn the Ubuntu disc as a .iso image?

~ Brett

---

### Post by richardward101 on 2006-04-19
You will need:

1) The file you downloaded from ubuntu.com
2) A CD Burner
3) CD burning software such as nero/easy cd creator, however i recomend you download [this]("http://www.mrbass.org/dvdrip/SetupDVDDecrypter_3.5.4.0.exe"), its called dvddecrypter but it also writes cds. Launch it and go Mode->Iso->Write, then click the little open button and open the image you downloaded from ubuntu.com, then click burn. a few minutes later you should have a ubuntu install cd!

Its not unlikely that you'll need to ask another question here before you get ubuntu up and running properly, so if you need to start windows, just take the cd out and reboot your PC.

Best of luck!

---

### Post by Zunkie on 2006-04-19
I did burn it already.  The problem I am having is opening it on my laptop (where I want to install ubuntu).  In the BIOS settings.  Is the order in which the systems are listed in the order in which theyre open?  If so then CD-ROM is listed first, then shouldnt it open the ubuntu CD without a problem?

---

### Post by richardward101 on 2006-04-19
What did you use to burn the CD?

The way it works is the first sector of the disk (the boot sector) contains code for the BIOS to find and execute. If there is no code there the BIOS looks at the next disk in its list and so on. Some burning software (eg nero I think) does not write this to the cd unless you enable it somewhere in the options.

The best way to check is as follows:
Find your XP install CD and stick it in your laptop.
Reboot.

You should see "Press any key to boot from CD..." appear for a few seconds, then windows will load normally.

If you see this message, that means that the BIOS is looking at the CD first and therefore the ubuntu disk must not have a bootsector (if this is the case either look for help on your cd burning software or use the link from my last post).

If you don't see the message then your bios probably isn't looking at your CD drive, you should maybe try and find an online help about your specific laptop BIOS.

Let us know if you get it working.

---

### Post by Kimm on 2006-04-19
When burning the .ISO you shouldnt just drag the CD onto the disk then click "burn"
You need to select something like "Burn CD-Image" then select the .ISO and let it do what it does.

Just in case, alot of people do this wrong.

---

### Post by Belathor on 2006-04-19
Go to [http://www.terabyteunlimited.com/utilities.html](http://www.terabyteunlimited.com/utilities.html) and download BurnCDCC if you want. It is designed exclusively to make iso cd's. Hope that helps!

---

