---
title: "Broadcom 4312 iMac 4,1 wireless not working."
date: 2010-06-23
forum: Apple Hardware Users
---

### Post by ncbowie on 2010-06-23
Here's the story.

When I first had partitioned, and formatted appropriately, I installed the newest version of Ubuntu available (Time of posting 10.4), on the partition made with bootcamp, rebooted into Linux with rEFIt 

Now once I booted into 10.4 I got to the desktop, it started asking me about restricted hardware drivers, so I went into System > Administration > Hardware Drivers, It then searched for the drivers, it found the STA driver, and the B43 driver, I am unable to allow both. So I went on to try ndiswrapper, I downloaded it off another pc, compiled and installed on the iMac. then I got the driver off the Leopard install disk, put that on my flash drive, extracted the files from the installer, put that on the flash drive, then I went back over to the machine in question, copied the file to the desktop, I used the cd command to navigate to the folder, then ran ndiswrapper -i bmcwl6.inf, I made sure that the inf and sys files were in there, so I didn't know what was going on exactly.\

So then I went into the software sources, and enabled the cd as a software source, then went into Synaptic, and installed the drivers, it said the install was successful, however when I go back to enable it, will still refuse to activate, I have looked all around for solutions, I have even checked out other threads on this matter. The funny thing seems to be, is that everyone, or almost everyone who has this card on their computer, are upgrading to 10.04, when it worked on a previous version.

Another thing, downgrading would be my last resort if nothing else works.

If you need any additional information, just ask.

I know you guys are here to help, I know that many others are frustrated by this problem too.

---

### Post by linuxopjemac on 2010-06-23
can you give me the output of 
```
lspci -vnn | grep 14e4
```

---

### Post by linuxopjemac on 2010-06-23
It seems that the open source b43 driver supports the g part of your card:

[http://linuxwireless.org/en/users/Drivers/b43#Supported_chip_types](http://linuxwireless.org/en/users/Drivers/b43#Supported_chip_types)

I would deinstall the STA driver and purge b43-fwcutter if you tried it before.

sudo apt-get remove bcmwl-kernel-source

Be connected to the internet with a cable:

```
sudo apt-get install b43-fwcutter
```
and let it do its job. I am not sure if it works, as in Debian it was broken. Hopefully it works in 10.04

---

### Post by ncbowie on 2010-06-23
> **linuxopjemac said:**
> It seems that the open source b43 driver supports the g part of your card:

[http://linuxwireless.org/en/users/Drivers/b43#Supported_chip_types](http://linuxwireless.org/en/users/Drivers/b43#Supported_chip_types)

I would deinstall the STA driver and purge b43-fwcutter if you tried it before.

sudo apt-get remove bcmwl-kernel-source

Be connected to the internet with a cable:

```
sudo apt-get install b43-fwcutter
```and let it do its job. I am not sure if it works, as in Debian it was broken. Hopefully it works in 10.04

I'll try this later, as I have found a workaround

I installed 9.10, inserted my 10.04 disk, and got the wireless working.

---

### Post by ncbowie on 2010-06-23
> **linuxopjemac said:**
> It seems that the open source b43 driver supports the g part of your card:

[http://linuxwireless.org/en/users/Drivers/b43#Supported_chip_types](http://linuxwireless.org/en/users/Drivers/b43#Supported_chip_types)

I would deinstall the STA driver and purge b43-fwcutter if you tried it before.

sudo apt-get remove bcmwl-kernel-source

Be connected to the internet with a cable:

```
sudo apt-get install b43-fwcutter
```and let it do its job. I am not sure if it works, as in Debian it was broken. Hopefully it works in 10.04

Using a wired connection isn't viable, when I upgrade to 10.04 again, I'll want to have the wireless working so I might consider copying files over, would this be okay?

On another note whenever I move a window, jagged edges paste over the screen, I know two things about this, it's the video card causing the, I don't have the appropriate drivers, plus, the linux support of ati cards stinks.

---

