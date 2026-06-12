---
title: "Install Ubuntu Studio on an external drive for Mac"
date: 2015-12-11
forum: Apple Hardware Users
---

### Post by Music_Guy on 2015-12-11
I have an iMac, running OSX. My daughter has a MacBook Air, also running OSX. I would like to install Ubuntu Studio (I understand it's based on Xubuntu) on a USB stick so that she can boot from the stick and use Studio. Can someone explain how to do this? I saw on some threads the rEFInd may be needed. Will that have to be installed on the mac, or can it be installed on the USB stick? BTW, I asked this same question in Ubuntu Studio; there were a few replies, but the suggestions did not solve the problem.

---

### Post by BobUgh on 2015-12-12
I'm a little reluctant to give advice here, but since no one has replied yet, here goes. If you are willing to try and fail, here is something to try. I have done some of these steps myself but not all of them. I would try all of it myself but for the time being I do not have unlimited internet connection.

First, before anything else, do you have backups of both machines? If no, I suggest using Time Machine, you can connect a large USB hard drive to the iMac, and if your iMac is connected to a wireless router, the Mac Book Air (MBA) can get backed up wirelessly, automatically and frequently. If you have the latest apple router (the tall one) (or recent time capsule), or many other non apple routers, the hard drive can be a network drive

You don't say how old your machines are and which versions of OSX they are running. Depending on their age they have usb-2 or usb-3, booting and running off of usb is going to be slow, with usb-2 very slow. If the machines have usb-3, be sure to get usb-3 memory sticks, and read their specs on read and write times. Many usb-3 memory sticks have read times over 100 MB/s with write times 10 or 20 MB/s but you can get faster if you pay more. (The MBA read and write speeds with its internal drive is typically 5 to 20 and possibly 100 times faster than using the average usb-3 stick.)

It might be best to do the following things on the MacBook Air if that is the target machine. If you want to try booting both the MBA and iMac off the usb stick, then you would create the usb on the machine that has the most recent OSX or hardware and the probability of this working goes down.

1. Have backups of the system(s).
2. On OSX, format the USB memory stick with Apple defaults that enable you to boot from it, single partition. Anything previously on that stick will be effectively deleted.
3. Go to the app store to re-install the OSX version you have, or if your OSX is old, you can ask to install the latest OSX
see [http://macs.about.com/od/usingyourmac/qt/How-To-Re-Download-Apps-From-The-Mac-App-Store.htm](http://macs.about.com/od/usingyourmac/qt/How-To-Re-Download-Apps-From-The-Mac-App-Store.htm)
3.2 Important: when the installer asks where to install it, point to the usb stick, not the internal drive.

When done with that, you should be able to boot from that stick, but the install is likely to be specific to that hardware, if done on the iMac, it may not work correctly on the MBA. But **when powering on, you will need to hold the "Option" OR "C" key down **until you get a choice of where to boot. I don't remember if step 2 or step 3 does this, but the memory stick will now have 3 partitions on it, with the EFI and Recovery partitions hidden.

I have done the above before. What I have not yet done myself is the following. So if you are adventurous try it and please report back.

4. Create the Ubuntu or Xubuntu install media, and with both it and the above stick in the machine, boot the machine holding "option". (if you are choosing to use a DVD and do this on the iMac, It may be OK but I'm not sure how much the installer looks at hardware when doing the installation.) [This may be optional, after booting into the *buntu installer, first go into *buntu disk utility and remove the OSX partition re-partitioning it with a linux partition and a linux swap partition.] But from this point on, just follow the basic instructions to install single boot *buntu to the stick where the OSX partition was; I would ignore any directions regarding the stuff regarding efi and grub. When you are done, you might be able to boot from the USB but you won't get GRUB giving you the choice, you will need to hold "Option" or "C" down while booting. And you shouldn't have modified anything on your hard drive. I'm not sure if this applies but after all this, you may need/want to boot into OSX and "bless" something on the *buntu stick.

Now that I have written the above, I'm eager to get to better internet access and try this myself soon.

Here's some links for additional references, you could really go down a rabbit hole following links they have:

#Create a bootable installer for OS X
[https://support.apple.com/en-us/HT201372](https://support.apple.com/en-us/HT201372)

[http://macs.about.com/od/OSXElCapitan/ss/Create-a-Bootable-OS-X-El-Capitan-Installer-on-a-USB-Flash-Drive.htm](http://macs.about.com/od/OSXElCapitan/ss/Create-a-Bootable-OS-X-El-Capitan-Installer-on-a-USB-Flash-Drive.htm)

[http://macs.about.com/od/usingyourmac/qt/How-To-Re-Download-Apps-From-The-Mac-App-Store.htm](http://macs.about.com/od/usingyourmac/qt/How-To-Re-Download-Apps-From-The-Mac-App-Store.htm)

[http://macs.about.com/od/usingyourmac/ss/Create-Your-Own-Os-X-Lion-Recovery-Hd-On-Any-Drive.htm](http://macs.about.com/od/usingyourmac/ss/Create-Your-Own-Os-X-Lion-Recovery-Hd-On-Any-Drive.htm)

[http://macs.about.com/od/Troubleshooting/fl/Starting-Up-From-the-OS-X-Recovery-HD-Volume.htm](http://macs.about.com/od/Troubleshooting/fl/Starting-Up-From-the-OS-X-Recovery-HD-Volume.htm)

And here are some boot up options on Macs
Option ---------- Access Mac Startup Manager
right Shift ------ Safe Boot, & disable auto login?
left Shift ------- Disable auto login
C - - - - - - --    Start from bootable media (DVD, CD, USB thumb drive)
T -------------    Enable Target Disk Mode
N -------------    NetBoot
X -------------    Force OSX bootup
D -------------    Apple Hardware test
Command-R  --  Boot from OS X Recovery Mode (Lion or later)
Command-Option-R -- Boot into Internet Recovery Mode (2011 or later)
Command-V ---------  Verbose Mode
Command-S ---------  Single User Mode
Command-Option-P-R ------	Reset PRAM or NVRAM
Hold down the Media Eject (&#9167;) key or F12 key, or mouse or trackpad button - eject

---

