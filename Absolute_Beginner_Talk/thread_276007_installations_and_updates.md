---
title: "installations and updates"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by hyby on 2006-10-12
Hi guys,

I dont have a readily avalibe internet connection to download and update my files, using apt-get. I was wondering is there a way i can update files and download programs off line?

also, i still cant get sound.

Why does linux always screw with me.

---

### Post by taurus on 2006-10-12
Okay, if you want others to help you with sound, you need to tell us what soundcard (onboard or PCI) do you have!  We are not mind readers here so I can't tell from "also, i still cant get sound." what the problem is besides you still can't get sound!  Try to be as specific as you can in describing it...  The more details you provide, the faster help you would get.

---

### Post by petersjm on 2006-10-12
As for offline-downloading, that's not possible as far as I'm aware. The whole concept of "downloading" something means you have to be online to do so. But perhaps you could download from another box, copy to CD and install that way?

---

### Post by PriceChild on 2006-10-12
[http://packages.ubuntu.com/](http://packages.ubuntu.com/) contains all the official packages which you may download and save to disc for offline instillation.

---

### Post by bfitzsimons on 2006-10-12
I have some files for wireless connection that I have downloaded onto another iMac in the office.  These were burned at slow speed to a CD and copied to my Ubuntu Desktop.

My hardware is: 
Apple iMac with 1GHz PowerPC G4 and 768 MB DDR SDRAM using dual boot: MacOSX 10.2.8 and Ubuntu 6.06 LTS;
Apple Airport Extreme Base Station using Controller Broadcom BCM4306;
I have wireless connection under the MacOS boot but not under the Ubuntu boot.

At Terminal, the comand $ ls Desktop, results in:
bcm43xx-20060125 [this is a folder with files in it], 
bcm43xx-fwcutterorig [this is a folder with files in it], 
bcm43xx-fwcutter-005 [this is folder with files in it], 
bcmwls.sys [this is a file], 
wl_apsta.0 [this is a file]

I have tried at Terminal the command $ sudo apt-get install bcm43xx-fwcutter, but this results in: 
Reading package lists ... Done
Building dependency tree ... Done
E: Couldn't find package bcm43xx-fwcutter

I have tried variations on the path to the folder (e.g. Desktop/<folder_name_here>) and variations on the folder name (e.g. just bcm43xx-fwcutter, also bcm43xx-fwcutterorig) - all give the same result.

How do I install these folders and files?  From the info found on other threads, I believe that these files, once installed, will allow me to hookup to the internet on the Ubuntu boot.

---

### Post by taurus on 2006-10-12
> **bfitzsimons said:**
> I have some files for wireless connection that I have downloaded onto another iMac in the office.  These were burned at slow speed to a CD and copied to my Ubuntu Desktop.

My hardware is: 
Apple iMac with 1GHz PowerPC G4 and 768 MB DDR SDRAM using dual boot: MacOSX 10.2.8 and Ubuntu 6.06 LTS;
Apple Airport Extreme Base Station using Controller Broadcom BCM4306;
I have wireless connection under the MacOS boot but not under the Ubuntu boot.

At Terminal, the comand $ ls Desktop, results in:
bcm43xx-20060125 [this is a folder with files in it], 
bcm43xx-fwcutterorig [this is a folder with files in it], 
bcm43xx-fwcutter-005 [this is folder with files in it], 
bcmwls.sys [this is a file], 
wl_apsta.0 [this is a file]

I have tried at Terminal the command $ sudo apt-get install bcm43xx-fwcutter, but this results in: 
Reading package lists ... Done
Building dependency tree ... Done
E: Couldn't find package bcm43xx-fwcutter

I have tried variations on the path to the folder (e.g. Desktop/<folder_name_here>) and variations on the folder name (e.g. just bcm43xx-fwcutter, also bcm43xx-fwcutterorig) - all give the same result.

How do I install these folders and files?  From the info found on other threads, I believe that these files, once installed, will allow me to hookup to the internet on the Ubuntu boot.

Would you please start a new thread?  Also, there is a section for MacOS users so perhaps you may want to post your questions in that section, getting more Mac experts there.

---

### Post by bfitzsimons on 2006-10-12
Thanks Taurus ... I'll do that, I'll start a new thread

---

