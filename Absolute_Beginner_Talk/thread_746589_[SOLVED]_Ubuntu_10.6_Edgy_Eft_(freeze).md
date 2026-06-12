---
title: "[SOLVED] Ubuntu 10.6 Edgy Eft (freeze)"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by Orcaporka on 2008-04-05
I have read through a couple of troubleshoot threads and none I have read seem ot address my particular problem.

I boot from the CD/DVD and I load the disk so that I have no problems getting to the screen with the two desktop items "install" and "examples." However if I click on the Install button nothing happens no install program starts up.

Any help would be appreciated thank you.

EDIT: 6.10 Edgy Eft  (sorry)

---

### Post by JoshuaRL on 2008-04-05
What hardware specs do you have?

Also, why are you using 6.10?  There's better ones out there, and unless you have to use it for a specific reason I wouldn't suggest it.

---

### Post by Orcaporka on 2008-04-05
> **JoshuaRL said:**
> What hardware specs do you have?

Also, why are you using 6.10?  There's better ones out there, and unless you have to use it for a specific reason I wouldn't suggest it.

I'm only using it because it came with a beginners guide.

As far as my specs are concerned its a Acer Aspire 3610
1.5GHz
256MB of RAM

thanks for replying.

---

### Post by mikewhatever on 2008-04-05
Not sure what's the problem, could be a bad burn or the iso, just wanted to remind that Edgy is no longer supported. [http://www.ubuntu.com/news/ubuntu610end-of-life](http://www.ubuntu.com/news/ubuntu610end-of-life)

---

### Post by NullHead on 2008-04-05
I STRONGLY suggest using 7.10 NOT 6.10. 7.10 has huge advantages to offer you, e.g more drivers, better support for more hardware, the list goes on.

EDIT: sorry I didn't know it came with a guide. I completely understand why you're using 6.10 now :D

---

### Post by Orcaporka on 2008-04-05
> **NullHead said:**
> I STRONGLY suggest using 7.10 NOT 6.10. 7.10 has huge advantages to offer you, e.g more drivers, better support for more hardware, the list goes on.


I downloaded 7.10 and burnt it to a disc but that also froze, even before the screen loaded properly.

---

### Post by ugm6hr on 2008-04-05
> **Orcaporka said:**
> I'm only using it because it came with a beginners guide.

As far as my specs are concerned its a Acer Aspire 3610
1.5GHz
256MB of RAM

thanks for replying.

The 256MB RAM might be the problem.

I would suggest using:
1. A more recent version (i.e. Gutsy, or wait a few weeks for the final Hardy)
2. AlternateCD to install
3. Perhaps even try Xubuntu rather than Ubuntu.

---

### Post by NullHead on 2008-04-05
Try running memtest86+. If everything is freezing like you say then I would suspect you have a bad stick of ram, but lest not jump to any conclusions just yet.

---

### Post by Orcaporka on 2008-04-05
> **NullHead said:**
> Try running memtest86+. If everything is freezing like you say then I would suspect you have a bad stick of ram, but lest not jump to any conclusions just yet.


Thank ill do the memory test now. I have been meaning to upgrade my RAM anyway as 256 is somewhat pushing it. Thanks for your help. Ill try the later version also.

---

### Post by JoshuaRL on 2008-04-05
Yeah, I agree.  You probably don't have enough RAM to run the Live CD.  Try getting the Alternate CD of Xubuntu like ugm6hr suggested and you should be fine.

And as far as a Beginners guide, we're here to answer any questions or problems you have.  I would suggest reading the stickies on the main Absolute Beginner Forum, and going from there.

Welcome to Ubuntu!

---

### Post by twist2b on 2008-04-05
please explain your freeze, sometimes its a graphics issues.... what i did to get 7.04 working (I recommend that one if you have HP or not popular computer OTHERWISE go with 7.10)

but what i did to get it working was i went straight to recovery mode after install and did this:
apt-get update
apt-get install nvidia-glx-new
after that WORKED PERFECTLY!
though i dont know if you have nvidia so whatever graphics you have try to update BEFORE using the OS

---

### Post by Orcaporka on 2008-04-06
Thanks for your help everyone, I downloaded the 7.10 text version and it all worked fine. I guess it was my RAM.

One new problem I am having is that I cannot connect to the internet. Ubuntu does not recognise any networks (wireless), I tried installing dirvers via ndiswrapper followed the protocol but it failed to change anything.

My computer is a notebook (Acer Aspire 3610) and I assume its an xp driver problem because if I booted to windows the wireless connected as soon as I put in my ESSID and password.

Thank you.

---

### Post by ugm6hr on 2008-04-06
Glad that worked.

Is it Ubuntu or Xubuntu you are using?

If you want wifi help...

Can you connect with wired internet?

Post the output from:
```
lshw -C network
```

You can either continue with this thread to sort this, or mark it solved and start a fresh one.

---

### Post by Orcaporka on 2008-04-06
> **ugm6hr said:**
> Glad that worked.

Is it Ubuntu or Xubuntu you are using?

If you want wifi help...

Can you connect with wired internet?

Post the output from:
```
lshw -C network
```

You can either continue with this thread to sort this, or mark it solved and start a fresh one.

Yes I can connect to wired and this is the output:

```


WARNING: you should run this program as super-user.
  *-network:0 DISABLED    
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:06:05.0
       logical name: eth0
       version: 02
       serial: 00:14:a4:2f:95:7b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=32 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth1
       version: 10
       serial: 00:0a:e4:e5:18:87
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.67 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes

```

---

### Post by ugm6hr on 2008-04-06
That one:
> product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
vendor: Broadcom Corporation

Try one of these:
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5BAirForce_One_54g%5D](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5BAirForce_One_54g%5D)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by Orcaporka on 2008-04-06
> **ugm6hr said:**
> That one:


Try one of these:
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5BAirForce_One_54g%5D](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5BAirForce_One_54g%5D)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

thanks,the first one was going well until it said "download the latest stable ndiswrapper" which I couldnt because I was no longer connected to the internet so I downloaded it to another computer then copied acroos via a USB stick, but I cannot get any further than that all I get it is:

tar: ndiswrapper-1.52.tar.gz: cannot open: no such file directory
tar: error is not recoverable: exiting now
tar: child returned status 2
tar: error exit delayed from previous errors.

And of I now cannot connect to the internet.
Should I have put the .gz file in a particular place?

---

### Post by ugm6hr on 2008-04-06
That How-to was written with Feisty in mind.  The ndiswrapper version in Feisty didn't work - hence needing the *latest* version.

I think the ndiswrapper in Gutsy is OK.

However, I am certain you will not be able to do this without installing, since you cannot blackilst the bcm43xx driver without a reboot - which you can't do on a LiveCD.

Actually - it is easier than that (on a HD install):

In Synaptic - search and install *ndisgtk*

Use the "Windows Wirless Driver" application in menu to select the .inf file (with .sys in the same directory).

```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```

Then reboot.

---

### Post by Orcaporka on 2008-04-06
> **ugm6hr said:**
> 
In Synaptic - search and install *ndisgtk*


I have searched for that however I found no results.

---

### Post by ugm6hr on 2008-04-06
> **Orcaporka said:**
> I have searched for that however I found no results.

Are you connected online at the time of booting?

---

### Post by Orcaporka on 2008-04-06
> **ugm6hr said:**
> Are you connected online at the time of booting?

no, I am no longer able to go online via wired, because I removed my network manager and network manager gnome (I assume)

---

### Post by ugm6hr on 2008-04-06
> **Orcaporka said:**
> no, I am no longer able to go online via wired, because I removed my network manager and network manager gnome (I assume)

Are you using the LiveCD, or have you installed?

I am confused.

If you are on a LiveCD, a reboot will fix everything back to default.

---

### Post by Orcaporka on 2008-04-06
> **ugm6hr said:**
> Are you using the LiveCD, or have you installed?

I am confused.

If you are on a LiveCD, a reboot will fix everything back to default.

I have installed.

---

### Post by Orcaporka on 2008-04-06
If I download bcm43xx-fwcutter and [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)


on this machine, then transfer it to my other one. Then install it and:

enable the use of Firmware for Broadcom 43xx chipset family. Will that work? or will what I have alreadyd one prevent it?

---

### Post by ugm6hr on 2008-04-06
> **Orcaporka said:**
> I have installed.

Sorry - that explains my confusion!

This should get you back online:
```
sudo apt-get install network-manager network-manager-gnome
```

Then ensure you have enabled all repos:
[http://ubuntuforums.org/showpost.php?p=4030951&postcount=16](http://ubuntuforums.org/showpost.php?p=4030951&postcount=16)

Then try finding ndisgtk again

---

### Post by ugm6hr on 2008-04-06
> **Orcaporka said:**
> If I download bcm43xx-fwcutter and [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)

on this machine, then transfer it to my other one. Then install it and:

enable the use of Firmware for Broadcom 43xx chipset family. Will that work? or will what I have alreadyd one prevent it?

Sorry - I didn't explain that fwcutter will work for you, albeit with intermittent reliability.

For that - you need to unblacklist bcx43xx (edit */etc/modprobe.d/blacklist* and remove the entry for bcm43xx)

Then just go to Restricted Drivers in the menu and enable the relevant firmware.

You still need NM reinstalled though.

---

### Post by Orcaporka on 2008-04-06
> **ugm6hr said:**
> Sorry - that explains my confusion!

This should get you back online:
```
sudo apt-get install network-manager network-manager-gnome
```

Then ensure you have enabled all repos:
[http://ubuntuforums.org/showpost.php?p=4030951&postcount=16](http://ubuntuforums.org/showpost.php?p=4030951&postcount=16)

Then try finding ndisgtk again

Thank you I'm very grateful, I have the wireless up and running now.
Sorry to take up your time.
Thanks again for all your help.

---

### Post by ugm6hr on 2008-04-06
> **Orcaporka said:**
> Thank you I'm very grateful, I have the wireless up and running now.
Sorry to take up your time.
Thanks again for all your help.

Did you use ndisgtk then? Or fw-cutter?

Perhaps you could mark this thread as Solved (see Thread tools above)

---

### Post by Orcaporka on 2008-04-06
> **ugm6hr said:**
> Did you use ndisgtk then? Or fw-cutter?

Perhaps you could mark this thread as Solved (see Thread tools above)

Well I put network manager etc. back in then I just enabled Broadcom firmware and the wired internet downloaded the update I needed and then my wireless worked.

Thanks once more.

---

