---
title: "Root - MBR - USB"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by N1N31NCHN41L5 on 2008-04-01
How do I access the root o a USB drive so I can install a OS to the MBR of the USB drive. I can't find anything in the forums and am at a loss. I just used gparted to reformat the USB drive into FAT 32. I am trying to install 1 of 3 different Linux Distros to the USB to run as the computer boots up. Back track Linux, Damn Small Linux and Puppy Linux. I have a 2 and a 4 GB thumb drive. Would prefer to do this on the 2, but the 2 is enabled with U3 technology which shows a 350mb portion of the drive as a cd rom, is this going to cause me a problem???

---

### Post by Tomatz on 2008-04-01
Have a look here :)

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by N1N31NCHN41L5 on 2008-04-01
> **Tomatz said:**
> Have a look here :)

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

That page is where my question originates from:


How to install BackTrack to a USB device:

   1. Download the (Portable Backtrack) USB BackTrack version
   2. Extract the Boot and BT3 folders to the root of your USB device
   3. Navigate to the Boot folder on your "USB device" and click bootinst.bat (click continue if the following error appears)

      BackTrack Error
   4. Follow the onscreen instructions to make the device bootable
   5. Once the USB install script has finished, reboot your computer and set your BIOS or Boot Menu to boot from the USB device

Enjoy!

---

### Post by Tomatz on 2008-04-01
> **N1N31NCHN41L5 said:**
> That page is where my question originates from:


How to install BackTrack to a USB device:

   1. Download the (Portable Backtrack) USB BackTrack version
   2. Extract the Boot and BT3 folders to the root of your USB device
   3. Navigate to the Boot folder on your "USB device" and click bootinst.bat (click continue if the following error appears)

      BackTrack Error
   4. Follow the onscreen instructions to make the device bootable
   5. Once the USB install script has finished, reboot your computer and set your BIOS or Boot Menu to boot from the USB device

Enjoy!

You need to explain yourself better.

Also the root of the drive just means the lowest point of the folder hierarchy. 

Maybe you need to format your thumb drive to fat16 (vfat)

U can use gparted for this :)

The walkthrough's on pendrive linux will tell you how to make the drive bootable

---

### Post by N1N31NCHN41L5 on 2008-04-01
> **Tomatz said:**
> You need to explain yourself better.

EXACTLY!!!!! That was a direct copy, paste of the ENTIRE tutorial from pendrivelinux.com and now maybe you can see where my confusion comes from???????

---

### Post by Tomatz on 2008-04-01
LOL!!!!!!

Thought it was you for a moment there.

:lolflag:

**I would format the drive first.**

Then

Boot into [B]windows
[/B]
Download backtrack

**Copy it (backtrack) into the pendrive and double click it**

(a .bat is a kind of msdos shell script)

:)

---

### Post by N1N31NCHN41L5 on 2008-04-01
Ok - so following the tutorial is getting me nowhere:

   1. Download the (Portable Backtrack) USB BackTrack version
   2. Extract the Boot and BT3 folders to the root of your USB device
   3. Navigate to the Boot folder on your "USB device" and click bootinst.bat (click continue if the following error appears)

      BackTrack Error
   4. Follow the onscreen instructions to make the device bootable
   5. Once the USB install script has finished, reboot your computer and set your BIOS or Boot Menu to boot from the USB device

Enjoy!

 this is what I get when i open up the file:

Welcome to Slax boot installer

This installer will setup disk F: to boot only Slax.

Warning! Master Boot Record (MBR) of the device F: wil be overwritten.
If F: is a partition on the same disk drive like your Windows installation,
then your Windows will not boot anymore. Be careful!

Press any key to continue, or kill this window [x] to abort...


This is what I get after I hit the enter key..........


Setting up boot record for F:, wait please...
The system cannot find the path specified.
Disk F: should be bootable now. Installation finished.

Read the information above and then press any key to exit...


What do i do to get it to properly load and after it does how do i get it to install and actually run the Linux......

---

### Post by Tomatz on 2008-04-02
> **N1N31NCHN41L5 said:**
> Ok - so following the tutorial is getting me nowhere:

   1. Download the (Portable Backtrack) USB BackTrack version
   2. Extract the Boot and BT3 folders to the root of your USB device
   3. Navigate to the Boot folder on your "USB device" and click bootinst.bat (click continue if the following error appears)

      BackTrack Error
   4. Follow the onscreen instructions to make the device bootable
   5. Once the USB install script has finished, reboot your computer and set your BIOS or Boot Menu to boot from the USB device

Enjoy!

 this is what I get when i open up the file:

Welcome to Slax boot installer

This installer will setup disk F: to boot only Slax.

Warning! Master Boot Record (MBR) of the device F: wil be overwritten.
If F: is a partition on the same disk drive like your Windows installation,
then your Windows will not boot anymore. Be careful!

Press any key to continue, or kill this window [x] to abort...


This is what I get after I hit the enter key..........


Setting up boot record for F:, wait please...
The system cannot find the path specified.
Disk F: should be bootable now. Installation finished.

Read the information above and then press any key to exit...


What do i do to get it to properly load and after it does how do i get it to install and actually run the Linux......

Are you doing this from windows?

---

### Post by bumanie on 2008-04-02
If you don't want the U3, you can go to the sandisk website and get a removal tool. You need to be sure you don't want it because you can't get it back once its removed. Personally, I found U3 extremely annoying. Not sure how it operates under linux. I removed U3 as soon as possible and did not try it under linux, so can't answer that specific question.

---

### Post by N1N31NCHN41L5 on 2008-04-02
I WISH i could say i was a complete idiot and had been doing this in Ubunutu - problem would be solved - but yes that was from inside windows....

---

### Post by Tomatz on 2008-04-02
> **N1N31NCHN41L5 said:**
> I WISH i could say i was a complete idiot and had been doing this in Ubunutu - problem would be solved - but yes that was from inside windows....

LOL

I've seen worse ;)

If your usb drive is partitioned that could be the problem. Windows see's partitions as separate drives (for some stupid reason) this may be confusing the installer.

All i can suggest is that you delete the partitions and try it again as one whole drive if this is the case.

Otherwise google the error message you get (which you have probably already done)

Sorry if that doesn't help but i've never used the "from windows" method before :(

---

### Post by N1N31NCHN41L5 on 2008-04-02
I bought a new 4 gb usb stick just in case that "usb cd rom" thing was the problem. I get the same error on the new drive. After this much time and having bragged how great Linux is - that i can get it to boot off a usb stick and go - i have to keep working it till i finally can get it to work.

---

### Post by Tomatz on 2008-04-02
> **N1N31NCHN41L5 said:**
> I bought a new 4 gb usb stick just in case that "usb cd rom" thing was the problem. I get the same error on the new drive. After this much time and having bragged how great Linux is - that i can get it to boot off a usb stick and go - i have to keep working it till i finally can get it to work.

Can you post the exact error message it gives you.

I will also try to do it myself so i can get a bit more knowledge on the process :)

---

### Post by N1N31NCHN41L5 on 2008-04-02
> **Tomatz said:**
> Can you post the exact error message it gives you.

I will also try to do it myself so i can get a bit more knowledge on the process :)

I'll be glad to. Will post the first chance i get after PT in the morning - so about 9-10 hours from now. At this momwnt the comp is trying to run Puppy using QMQC VM ware. I will not quit this project till i can boot Linux off USB and run Linux in a comp that is running windows simultaneously. Knowldge will come from experience and Damn*t , i wanna learn - lol.   

Thanks for your help so far. I REALLY appreciate it.

---

### Post by Tomatz on 2008-04-02
> **N1N31NCHN41L5 said:**
> I'll be glad to. Will post the first chance i get after PT in the morning - so about 9-10 hours from now. At this momwnt the comp is trying to run Puppy using QMQC VM ware. I will not quit this project till i can boot Linux off USB and run Linux in a comp that is running windows simultaneously. Knowldge will come from experience and Damn*t , i wanna learn - lol.   

Thanks for your help so far. I REALLY appreciate it.

It's cool ;)

The best way to learn anything is trial and error :)

---

### Post by N1N31NCHN41L5 on 2008-04-02
> **Tomatz said:**
> It's cool ;)

The best way to learn anything is trial and error :)

I must have been really tired, if you read the previous posts you will see what it says in windows as i run the dos thingy. when i load the comp up to boot off usb it tells me it has a invalid disk. and thats as far as it goes.....

---

### Post by N1N31NCHN41L5 on 2008-04-05
ok so i still cant boot from USB but have found out about a much bettter way to show of Linux. use vmware to run a Linux distro in windows. BUT i cant get ANY Distro of linux past the CLI. they will run like that but that is it. This problem exists in xununtu, Back Track and Puppy. Back Track gives me the most usefull info of all: Cannot find monitor. Any ideas??????

---

### Post by Tomatz on 2008-04-05
Sorry mate i haven't tried to install it myself yet i've had no time :(

I will try to install it today and post back results :)

---

### Post by N1N31NCHN41L5 on 2008-04-05
> **Tomatz said:**
> Sorry mate i haven't tried to install it myself yet i've had no time :(

I will try to install it today and post back results :)

many thanx

---

