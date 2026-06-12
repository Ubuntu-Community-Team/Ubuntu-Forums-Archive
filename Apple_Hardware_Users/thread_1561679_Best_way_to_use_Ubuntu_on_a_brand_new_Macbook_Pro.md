---
title: "Best way to use Ubuntu on a brand new Macbook Pro?"
date: 2010-08-26
forum: Apple Hardware Users
---

### Post by Andy06 on 2010-08-26
I have about 4 years experience with Ubuntu, but 0 with Macbooks.

I am now about to try and install Ubuntu on a mint new Macbook Pro however all of the (community) documentation, stickies and FAQs have me really scared.

1) What is the best way to run Ubuntu on a Macbook?
a)Full (internal) dual boot
b)USB/SD/external live/full install
c)Virtualisation (virtualbox? Parallels? VMware Fusion?)

2)The community documentation says half the things are not expected to work out of the box, why? It works perfectly fine on new laptops of almost all manufacturers. What is so different here?

3)I keep reading conflicting opinion on whether or not its possible to boot off a external USB HDD/flash drive/SD card. Some say not possible at all, some say it is possible with GUID or whatever and other says it is even possible with hybrid MBR. So what's the bottom line here, is it or is it not doable?

This is not going to be as seamless and smooth as installing on a normal PC is it :(

Thanks a lot guys

---

### Post by dngfng on 2010-08-27
Hi

I just went through the process its best to dual boot with rEFIt. And use Mac OSX internal partitioning tool. 

This guide is really great - just follow the steps and you are good to go.

[http://lifehacker.com/5531037/how-to-triple+boot-your-mac-with-windows-and-linux-no-boot-camp-required](http://lifehacker.com/5531037/how-to-triple+boot-your-mac-with-windows-and-linux-no-boot-camp-required)

If you don't want to install windows just skip that step and only make 3 partitions os x, root and linux swap.

After you installed ubuntu follow the steps (depending on your macbook pro model) here:

[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

We found some Fan Control issues witch SwedishWings [macfanctl]("http://ubuntuforums.org/showpost.php?p=9765062&postcount=24") takes care of pretty well.

> 
This is not going to be as seamless and smooth as installing on a normal PC is it :sad:
I never used OS X before but the process is just as easy if not easier then installing on a regular PC (at least when multi booting).

Let me know if you need any help.

---

### Post by Andy06 on 2010-08-28
Ok I really want to try it out as a Live system first. 

How do I go about booting the system from a Live USB?

Thanks

---

### Post by Lars Noodén on 2010-08-28
The advice to use rEFIt is good.  It makes dual boot OS X / Linux very convenient.  

If you want a live CD, you can burn one.  I would recommend investing in a CD-RW for a few EUR.  Be careful not to scratch it and it should be good for hundreds of tests.  

It can be useful to put the Ubuntu home directory in a separate partition and format it as HFS+.  Then you can still access it from OS X.  You'll want these tools for that:

 hfsplus - Tools to access HFS+ formatted volumes
 hfsutils - Tools for reading and writing Macintosh volumes
 hfsprogs - mkfs and fsck for HFS and HFS+ file systems

Then in OS X, you'll want to change your UID to match your linux UID so that you may read and write the files in your linux home.  The method to do that changes from version to version in OS X.  Currently it can be done using [dscl](http://osxdaily.com/2009/02/19/mac-os-x-change-your-user-id/) and there are howtos and mini-tutorials around for guidance.  

Ubuntu currently won't deal with HFS during the installation so that has to be done afterwards.  Use caution.  Measure twice, format once.  

Occasionally the disk needs to be fsck'd.  Ubuntu can't handle that for HFS automatically on startup.  So if the desktop environment seems to lock up after logging in, restart and log in to OS X and then reboot back to linux.

As far as both at the same time I know people that do a lot of network development on linux using the FOSS edition of VirtualBox run with OS X as the host.  Myself, my needs are met by qemu but I prefer to run natively because I do no kernel work.

---

### Post by Andy06 on 2010-08-28
What about Live USB? Any way to boot off that?
Optical media (CD/DVD) is not practical for me since I'll have to carry that awkward shaped thing every where I go.

USB/SD card would be far more ideal

Thanks

---

### Post by aysiu on 2010-08-29
> **Andy06 said:**
> 
1) What is the best way to run Ubuntu on a Macbook?
a)Full (internal) dual boot
b)USB/SD/external live/full install
c)Virtualisation (virtualbox? Parallels? VMware Fusion?)
 a) This is the best way

b) USB/SD/external will not work

c) Virtualization is okay, but the multi-touch on the trackpad isn't as responsive as a full install

---

### Post by Andy06 on 2011-01-13
So there is no way to run a LiveUSB on a Macbook Pro?? :O

---

### Post by sudo_0 on 2011-01-14
> **Andy06 said:**
> So there is no way to run a LiveUSB on a Macbook Pro?? :O



not according to this: [http://ubuntuforums.org/archive/index.php/t-419427.html](http://ubuntuforums.org/archive/index.php/t-419427.html)
*link to how to live usb/MBPro


hmm.... 


sudo apt-get install brain :)

---

### Post by zasf on 2011-01-15
> **Andy06 said:**
> So there is no way to run a LiveUSB on a Macbook Pro?? :O

I have a Macbookpro 7.1 and can boot with my usb stick by choosing it at boot time with rEFIt. I manually partitioned and debostrapped a system on it, but maybe it works even with the one created with the ubuntu utility, I haven't tried tough.

---

### Post by sydney.unc on 2011-01-15
i borrowed a friends Ubuntu 10.10 disc and am running it in dual boot with OS X

however, if your Mac is new new (i received mine for Christmas) and it is 6,2 it is unable to connect to the internet (both wirelessly and through ethernet) and a friend it working on making me a network driver

---

