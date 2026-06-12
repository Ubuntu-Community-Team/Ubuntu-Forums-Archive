---
title: "Wireless unstable conection"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by jerrykun on 2007-06-18
I recently install ubuntu fiesty on my acer labtop aspire 5610z i followed this steps  [HTML] Install Ubuntu on Acer Aspire 5610Z or 5610-2966
I just received my new Acer 5610Z/5610-2966 and I thought I would share my Ubuntu install experience. This Acer is a great little laptop by the way.

This laptop comes with Vista Home installed, so the first step is to backup Vista. Just in case I want to sell it to someone that wants Vista installed on it in the future.

How to back up Vista:

1. Boot up your computer and open Acer eRecovery.
2. Pop in a DVD-R or DVD+R disk.
3. Click on Burn Disk at the bottom of eRecovery.
4. Click on Factory Restore Option at the top.
5. It will burn your DVD.

The Aspire comes with a Vista Upgrade Anywhere disk. You will need this disk when you want to restore Vista. If you ever need to restore, it is a simple but time consuming process. You will need to use the Vista Upgrade Anywhere disk to install Vista. This will format your disk and remove the Grub boot loader. Then you can boot off of the Factory Restore DVD you made and restore Vista with all the Acer extras and drivers.

Now the fun part.

Install Ubuntu:

1. Press F2 on Boot to access the Bios settings.
2. Set the DVD as the first boot device and save the Bios changes.
3. Pop in your Ubuntu install disk (You Should Use 7.04, but I used 6.10)
4. Erase entire drive and install (note my drive was partitioned into three partions for Vista. Partition 1 was a Vista Restore partition. You gain almost 9 Gig of HD space by using Ubuntu instead of Vista. Sweet!)

What does not work?
1. Special Laptop Buttons that line the right and top of keyboard. They are shortcuts to access the Windows Media Player and IE,Email,Word processor.
2. Built in Media Card Reader (Under 6.10 I heard it works under 7.04, but I have not tested it.)
3. High Resolution Display is at 1024x760 until you install 915resolution package with Synaptic.
4. I was not able to test the modem, so I don't know if that works.
5. Wireless does not work out of the box because Acer uses a Broadcom Airforce One Card. Broadcom does not offer native Linux Drivers. Let me give you the fix for that.

How to get wireless working:

(You will need to be connected to the internet by a wired connection)
1. Install using Synaptic ndiswrapper-utils-1.8 and wifi-radar.
2. Download and expand the 32bit driver I have attached to this post. If you need the 64bit driver you can check the Ubuntu forums and you will find one. (You may need to be signed into the Ubuntu forums to download my attached file.)
3. Open a terminal window and navigate to driver folder and type:
Code:

sudo ndiswrapper -i bcmwl5.inf

4.
Code:

sudo modprobe ndiswrapper

5.
Code:

sudo gedit /etc/modprobe.d/blacklist

6. Blacklist the old broadcom driver by typing in the following at the bottom of the text file:
Code:

blacklist bcm43xx

7. Save Text File.
8. To Make your wireless start up with each boot you will need to add ndiswrapper to the modules that start at boot time:
Code:

sudo gedit /etc/modules

9. At the bottom of the text file type:
Code:

ndiswrapper

10. Save Text File
11. Restart you laptop
12. Use wifi-radar to locate and connect to your wireless router. wifi-radar is found under Applications>Internet in the upper left hand corner of your Ubuntu Desktop.

Ubuntu works great on this Laptop. It uses both processors and seems very smooth and stable.
If anyone has any additional notes please add them below.
Attached Files
File Type: gz 	Broadcom Driver 32bit.tar.gz (264.5 KB, 11 views)  [/HTML]but now its extremly hard to get connected and when i do get connected it doesn't last very long probably for like about 1 min tops 2 min. any advice or step by step guide

---

### Post by jerrykun on 2007-06-19
I also cant see videos anytime i open any kind of videos it closes intanly and my xorg.config its empty i install aoutmatix compile my kernell and i still have the problems i really need help

---

