---
title: "Bootable Installs: USB, SD, ExpressCard?"
date: 2010-01-31
forum: Apple Hardware Users
---

### Post by TacticalToast on 2010-01-31
I have searched for a few days now and it seems this forum is the most active when it comes to linux questions so here goes. 

I have a MacbookPro5,1 and have been looking into various ways of running a linux distro in non-legacy mode, aka through EFI. I was thinking Fedora 12 (gasp) because it supports EFI booting on MBR formatted drives BUT not on a GUID drive (correct me if im wrong). The biggest reason I want to use EFI is because I want to use the 9400m instead of the 9600 card which apparently can be accomplished by entering the correct PCI ID into the xorg.conf file.

So heres what I was thinking...

**Requirements:**
- I'd like to avoid using the internal drive (running 10.6.2) but am open to it if no other options exist
- I need to be able to boot via EFI (and able to select it by holding Option at boot)

**Variables:**
- USB and SDHC cards my AFT PROExpress-7 card reader are bootable via EFI. I understand that these types of flash memory (SD especially) were not designed to run operating systems and the amount of read/writes could kill the drive off quickly if configured wrong.
- I am unsure of whether or not the ExpressCard/34 slot can boot off an ExpressCard SSD. I have been looking at the [MyDigitalSSD 32GB]("http://www.mydigitaldiscount.com/SPD/mydigitalssd-32gb-expresscard-34-ssd-solid-state-disk--800009A5-1237840218.jsp") card because it is much faster than the older versions of ExpressCard ssd's and is relatively cheap. *Can anyone comment on this or other ExpressCard SSD's?*

**NOTE:**
- I know about rEFIt but I don't think it helps me in this case (booting XP yes, but if i want to boot linux EFI i don't think so)
- As mentioned above, I am unsure of what are the requirements for booting a linux distro via EFI when it comes to type of partitioning scheme and what bootloader to install (grub2 or elilo) for a Macbook Pro

I'm open to any/all suggestions and will try to document everything I do to update the sparse Wiki's when it comes to this topic. Thanks in advance!

---

### Post by tom4everitt on 2010-02-01
Here's a guide for how to get grub2 to boot your system (instead of the regular mac boot loader). So the first thing you will see at boot is grub2, which can boot linux as well as mac. 

[http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook)

I only managed to make this boot OS X, not linux (graphics problem), but it might be worth a shot. (I'm sure you understand that you risk your computers bootability by experimenting with this stuff.)

This does not quite fit into your requirements (no option key involved). I don't know if that is possible.

---

### Post by TacticalToast on 2010-02-01
Hey,
Installing grub2 to boot both OS's was something I hadn't thought about.

The reason I mentioned 'holding Option at boot' is because with the stock firmware,  this brings you to a screen which let's you select which volume to boot. The same way you'd boot into BootCamp for example.

At this time I'd stray away from using grub2 as the only bootloader on the mac but do you/or anyone else know if its possible to use the existing apple firmware to select a drive or partition that has grub2 installed? I would just set the time out to 1sec or something and not worry about it.

For example, if you installed ubuntu (or any other kernel) with EFI booting capabilities to an external drive (whether be USB, SD, ExpressCard, FW, etc) would you need a bootloader on that external drive? OR could the stock firmware boot it?

---

### Post by tom4everitt on 2010-02-02
Okay, I see. I don't really know how the option-key menu is working, but I believe that you usually get a "windows"-entry if you install linux. At least I get that on my own computer now (just checked), so chances are good you don't have to do any configuration at all for that. 

But you will of course have to install grub (or other boot loader) for the linux system. The stock firmware is only chainloading linux. But I see no reason why you would not want to do this, its as easy as not unchecking the box with install boot loader during installation (and set it to the right partition of course). 


Also I would recommend you to at least have refit installed during the installation phaze, since it comes with a partion sync tool which is really handy. Not installing refit/not discovering its sync tool is in fact the most common reason people write here about there computers not being bootable after linux installation. 

And once you have it you might discover that it is not so bad at all :) (just make sure you get the refit menu at every boot before you go ahead with the installation.)

---

### Post by TacticalToast on 2010-02-02
I never though to install rEFIt as a failsafe of sorts. It makes a lot of sense tho.

I understand that the stock firmware is chainloading linux, but just to be clear: Regardless of what drive I have linux installed on, I should still have a bootloader for the linux install?

---

### Post by tom4everitt on 2010-02-03
Yes, you should install boot loader. But install it to the same partition that you are installing linux to. If that doesn't work you can try to install it to (hd0) also (from a live cd).

The community guides generally hold high quality:
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

---

