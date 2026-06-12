---
title: "How to Boot Linux from USB on Macbook Pro"
date: 2007-04-23
forum: Apple Intel Users
---

### Post by bcrawfor on 2007-04-23
*******I know I did not use uBuntu for this, but the information is still relevant....and perhaps even possible with uBuntu.

I am fairly unschooled in the world of Linux, and I have been dieing to learn more about Linux for some time. So, about a week ago I began researching how to run Live Linux distributions on my Macbook Pro. 

Using a nifty EFI extension called rEFIt, I discovered that booting live linux distributions on a Macbook Pro is possible. Also, I discovered that Slax recognizes many of the Macbook Pro's features (such as ethernet and Bluetooth) straight away. 

HOWEVER, being the greedy man I am, simply booting into live linux on my macbook pro was not enough. I HAD to know if booting a live linux distro on my Macbook Pro was possible from USB. (Macbook Pro's supposedly do not support booting from USB) 

After 2 days of messing around, I discovered this: Yes, it is possible...well sort of. 

This is what I did. 

1. Dowload and install rEFIt, if it is not already installed on your Macbook Pro. refit.sourceforge.net/ 

2. Download Slax Killbill Edition 5.1.8.1 and burn it to a CD 

3. Place the Slax CD in your disc drive. Reboot your macbook pro and boot (from the rEFIt menu) into Slax Linux. 

4. Follow these instructions on formating a USB flash drive to boot slax: 
***.slax.org/forum/viewtopic.php?t=7094 (replace *** with www) 

5. This is the part where I tried something random and it payed off. I downloaded, from the Slax website, the Slax Boot CD (version 5.1. and burned it to a disc. The boot cd redirects your computer to boot from USB, in case it does not support USB booting. 

6. Now, place the Slax Boot Disc into your disc drive and plug in your Slax USB drive. Reboot your Macbook Pro. When the rEFIt menu loads, select the Linux Boot CD to boot from. (ignore the USB Drive, which is a choice. It will not load) 

7. Now, watch as Slax boots effectively. Slax will boot MUCH faster from flash memory than from a CD. It also runs much smoother. 

Now, as far as I know, no one has been succesful booting Linux from USB on a Macbook Pro. (or booting any OS from USB on a Macbook Pro) Is it possible that Linux distributions ARE completely compatible with the Macbook Pro, they must just use a device---such as a linux boot disc---to redirect the system during the boot process? 

I think I have stumbled onto something, due to my simplistic approach to booting linux. But if booting linux from USB is possible with a boot disc, I wouldnt mind installing it to an external USB HD to use occasionally ------even if I have to stick a disc into my drive to get the Linux OS to boot. 

I look forward to some interesting comments on this topic.

---

### Post by koni2005 on 2007-04-23
I did succesfully install and boot Linux - openSUSE 10.2 - from an external USB drive plugged into my MacBook Pro 2.16Ghz Core Duo. It works flawlessly, just install it from the Live DVD onto the drive. SUSE configures GRUB correctly and rEFIt recognizes the USB installation.

I would love to do the same thing with Ubuntu 7.04. Anyone has an idea of how to do it?

---

### Post by bcrawfor on 2007-04-23
what about KDE. I love suse's KDE interface. Do you think that KDE would work from USB as well?

---

### Post by ronocdh on 2007-04-23
> **bcrawfor said:**
> what about KDE. I love suse's KDE interface. Do you think that KDE would work from USB as well?
I'm sure that if we get Ubuntu working (booting from USB), getting the same performance for Kubuntu would be incredibly trivial. The two really aren't all that different.

---

### Post by erkker on 2007-04-23
I tried to install feisty on an usb ipod (5th gen 30GB) and use that to boot a new MacBook Pro 2.33 Ghz C2D w/ 2GB ram.  I used the alternate 1386 cd (I really like the old debian installer).  

After installing rEFIt I downloaded and burned a i386 Feisty install disc.  rEFIt recognized the cd and booted into the install.  Here I ran into my first problem:  If I had the iPod attached before the Ubuntu install menu popped up the keyboard was unresponsive.  It took a few cold boots for that to clear up.  At that point I checked the CD and it appeared to be fine.

Restarted booted into the Ubuntu install CD.  At the initial option screen plugged in the ipod, after checking to make sure the keyboard worked.  Install went fine until the partition manager popped up. The installer recognized the ipod but not any of its partitions.  Nonetheless I pressed on hoping for the best.  I formatted the ipod into a Fat32 partition for music, and a ext3 partition for ubuntu.  The install continued withour a hitch.  on reboot rEFIt recognized the linux partition and offered to boot from it.  However when I chose that option I got a black screen with yellow text listing about 10 errors and a warning message that Apple had poor USB boot support.

Oh well.  I reformatted my ipod with the Apple restore untility and used fdisk to format the standard fat32 into a smaller fat disk and a ext3 disk.  Perhaps it will work better this time.  

Will update as things improve (or I fail spectacularly).

In unrelated news feisty works great on my friends 4 year old Gateway 2Ghz celeron, 512MB laptop.  That will show XP to lose its little mind and corrupt a harddrive beyond mountable capabilities :)

-E

---

### Post by jlinux1 on 2008-03-01
I also was able to boot slax Killbill edition from a usb flash drive on a macbook pro. However I could not set up the wireless yet. Does anyone know how to set that up? I am new to linux!:)

---

### Post by cyberdork33 on 2008-03-01
> **jlinux1 said:**
> I also was able to boot slax Killbill edition from a usb flash drive on a macbook pro. However I could not set up the wireless yet. Does anyone know how to set that up? I am new to linux!:)
It would be beneficial to let us know what hardware (and version of the hardware) you are using... 

How you have installed to the USB drive to enable it to boot would also be helpful as that has been a problem for most users.

---

### Post by jlinux1 on 2008-03-02
AirPort Card Information:
  Wireless Card Type:	AirPort Extreme  (0x168C, 0x86)
  Wireless Card Locale:	USA
  Wireless Card Firmware Version:	1.1.9.3
  Current Wireless Network:	Apple Network 220e31
  Wireless Channel:	11

bash-3.1# iwconfig
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11a  ESSID:""
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:15 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.
I was able to extract slax on to a usb thumbdrive and run make_disk.sh in linux. Also I have to use a boot disk in order to use the usb drive. I hope that will shed some light!

---

### Post by cyberdork33 on 2008-03-02
I meant what type of Mac you have. There are different types of Airport cards, so the fact that it is an airport card doesn't help.

---

### Post by jlinux1 on 2008-03-02
Hardware Overview:

  Model Name:	MacBook Pro 15"
  Model Identifier:	MacBookPro1,1
  Processor Name:	Intel Core Duo
  Processor Speed:	2.16 GHz
  Number Of Processors:	1
  Total Number Of Cores:	2
  L2 Cache (per processor):	2 MB
  Memory:	2 GB
  Bus Speed:	667 MHz
  Boot ROM Version:	MBP11.0055.B08
  SMC Version:	1.2f10

---

### Post by cyberdork33 on 2008-03-02
> **jlinux1 said:**
> Hardware Overview:

  Model Name:    MacBook Pro 15"
  Model Identifier:    MacBookPro1,1
  Processor Name:    Intel Core Duo
  Processor Speed:    2.16 GHz
  Number Of Processors:    1
  Total Number Of Cores:    2
  L2 Cache (per processor):    2 MB
  Memory:    2 GB
  Bus Speed:    667 MHz
  Boot ROM Version:    MBP11.0055.B08
  SMC Version:    1.2f10
I am pretty sure you need this:
[https://wiki.ubuntu.com/MacBookPro](https://wiki.ubuntu.com/MacBookPro)

---

