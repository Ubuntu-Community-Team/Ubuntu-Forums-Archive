---
title: "Triple Booting (Spoonfeed Me)"
date: 2016-03-25
forum: Apple Hardware Users
---

### Post by PCPotato11 on 2016-03-25
Hello, 

I am no pro in computer systems, however, I am very open to learning. I just recently learned in the past month that triple booting with windows, linux and mac would be possible without the using of a virtual loader. That being said, I've done a whole bunch of research, but cant quite understand the steps 100%.

I thought it was only possible to do so by first installing Linux, then loading Windows and OSX, however, my current research tells me otherwise. 

I am not understanding the whole installation process and the booting process. 

Would it be too much of a hassle to ask someone to walk me through it step by step? 

Any help is super appreciated <3

---

### Post by coffeecat on 2016-03-25
I've moved this thread into the Apple hardware users sub-forum, in case the triple-booting you envisage will be on Apple hardware, as I am sure that someone with Apple Mac experience will be able to answer your questions. If, however, you were contemplating installing OSX on non-Apple hardware, we will not be able to help you, as this would involve circumventing the Apple EULA.

---

### Post by Bucky Ball on 2016-03-25
Windows first is the most pain-free and rule-of-thumb with dual (or more) boots from scratch. Know nothing about OSx.

---

### Post by LostFarmer on 2016-03-25
Exactly what MAC do you have, the process is different for each.  Some are somewhat easy while others are harder.  What MS Windows do you have to install ?

On my Mac Book Pro early 2011 8.4, I installed Max OS, then Windows7 via boot camp and last Linux.  OSX and linux installed in EFI mode and Win7 installed in MBR mode.  Could not get Win7 to install in EFI mode and Linux had no display in MBR mode.  Have to use the option key during boot to select a non-default OS to boot.

---

### Post by Bob_Bruce on 2016-04-10
> **LostFarmer said:**
> Exactly what MAC do you have, the process is different for each.  Some are somewhat easy while others are harder.  What MS Windows do you have to install ?

On my Mac Book Pro early 2011 8.4, I installed Max OS, then Windows7 via boot camp and last Linux.  OSX and linux installed in EFI mode and Win7 installed in MBR mode.  Could not get Win7 to install in EFI mode and Linux had no display in MBR mode.  Have to use the option key during boot to select a non-default OS to boot.

Have you tried installing rEFInd? It allows you to select whatever system is installed on whatever drives you have attached. Works great on my 2009 iMac. 

Here's the link to the site: [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

The easiest way to install it is from Linux using these commands in a terminal window:

sudo apt-add-repository ppa:rodsmith/refind
sudo apt-get update
sudo apt-get install refind

Then just reboot and you should be able to select the OS of your choice from the rEFInd graphical interface.

---

