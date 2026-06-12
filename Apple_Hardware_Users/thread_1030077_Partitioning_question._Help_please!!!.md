---
title: "Partitioning question. Help please!!!"
date: 2009-01-04
forum: Apple Hardware Users
---

### Post by joka. on 2009-01-04
After much research on the new Macbook Pro 5,1 and on Ubuntu 8.10 I've decided to get the new MBP and triple boot with XP or Vista and Ubuntu 8.10. However, right when I was about to purchase the laptop today in the store, I had a few last min. questions and noticed/was told that Bootcamp was only able to partition the hard drive only up to 50% [e.g. 50% of the hard drive would be for OS X and 50% for another partition]. I want to make the OS X's partition even smaller than that. So my questions are:
1. Is it true Bootcamp can only partition it up to 50% or am I missing something?
2. What partitioning programs did you use? [Bootcamp, rEFIt, grub, etc.] Did you dual or triple boot?
3. Which one would you suggest I use for triple booting? [Easiest to use and least amount of problems]
4. If you can provide me with steps that would be awesome. [I know there are a few pages in the Ubuntu forums that explains it, but I found that some people ended up having problems after following those instructions. If you can provide me with the link with the least amount of problems.]

Thanks for all your help!

---

### Post by pxwpxw on 2009-01-04
> **joka. said:**
> After much research on the new Macbook Pro 5,1 and on Ubuntu 8.10 I've decided to get the new MBP and triple boot with XP or Vista and Ubuntu 8.10. However, right when I was about to purchase the laptop today in the store, I had a few last min. questions and noticed/was told that Bootcamp was only able to partition the hard drive only up to 50% [e.g. 50% of the hard drive would be for OS X and 50% for another partition]. I want to make the OS X's partition even smaller than that. So my questions are:
1. Is it true Bootcamp can only partition it up to 50% or am I missing something?
2. What partitioning programs did you use? [Bootcamp, rEFIt, grub, etc.] Did you dual or triple boot?
3. Which one would you suggest I use for triple booting? [Easiest to use and least amount of problems]
4. If you can provide me with steps that would be awesome. [I know there are a few pages in the Ubuntu forums that explains it, but I found that some people ended up having problems after following those instructions. If you can provide me with the link with the least amount of problems.]

Thanks for all your help!
Have a look at this help doc, the MacOSX/Vista/Ubuntu partitioning info.
It is under review but should help, and has an uplink to the main doc.

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

Note that the partitioning for XP is more difficult than for Vista.

There is also a link there to Apple BootCamp pdf, re the min size for MacOSX partition. I have managed to get MacOSX (Tiger) on an 8GB usb stick, but not using Boot Camp.

---

### Post by joka. on 2009-01-04
> **pxwpxw said:**
> Have a look at this help doc, the MacOSX/Vista/Ubuntu partitioning info.
It is under review but should help, and has an uplink to the main doc.

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

Note that the partitioning for XP is more difficult than for Vista.

There is also a link there to Apple BootCamp pdf, re the min size for MacOSX partition. I have managed to get MacOSX (Tiger) on an 8GB usb stick, but not using Boot Camp.

Thanks for the link, it's a bit clearer than the others I've came across.

For the link on the BootCamp: [http://www.macgeekery.com/tips/cli/nondestructively_resizing_volumes](http://www.macgeekery.com/tips/cli/nondestructively_resizing_volumes)
I'm assuming the author is re-partitioning the drives in Linux after installing dual or triple boot? Or is he doing this in Mac OS X? [This would also be my first Mac so I'm not familiar with all the commands in it.]

I was originally planning on booting OS X on an external hard drive or USB stick, however I realized that the MBP 5,1 have the multi-touch pad, so I'm guessing if I do end up removing the OS X, it would no longer be able to operate the multi-touch?

---

### Post by pxwpxw on 2009-01-04
> **joka. said:**
> Thanks for the link, it's a bit clearer than the others I've came across.

For the link on the BootCamp: [http://www.macgeekery.com/tips/cli/nondestructively_resizing_volumes](http://www.macgeekery.com/tips/cli/nondestructively_resizing_volumes)
I'm assuming the author is re-partitioning the drives in Linux after installing dual or triple boot? Or is he doing this in Mac OS X? [This would also be my first Mac so I'm not familiar with all the commands in it.]

Sory, thats the wrong link, I meant this one, (I have no comment on the  resizing reference). You can use the GUI for what you want.

Bootcamp Installation Guide pdf from here -
[http://www.apple.com/support/bootcamp/](http://www.apple.com/support/bootcamp/)

> 
I was originally planning on booting OS X on an external hard drive or USB stick, however I realized that the MBP 5,1 have the multi-touch pad, so I'm guessing if I do end up removing the OS X, it would no longer be able to operate the multi-touch?

There has been a lot of work done in this forum getting the multi touch pad working for ubuntu, you should find some threads by searching - I don't have it here so I cant be more specific.

You might have to take the plunge and get the MacBook Pro to answer some of your qureies :)

---

### Post by suda on 2009-01-04
You may also want to go to the Apple Web site under Support, then Mac OS, and you'll find a lot of info on Boot Camp. Here's the link: [http://www.apple.com/support/osfamily/](http://www.apple.com/support/osfamily/)

See right hand side of page.

---

### Post by cyberdork33 on 2009-01-05
> **joka. said:**
> 1. Is it true Bootcamp can only partition it up to 50% or am I missing something?
It is very well the case, but there are several other ways to partition, so it doesn't really matter.
> **joka. said:**
> 2. What partitioning programs did you use? [Bootcamp, rEFIt, grub, etc.] Did you dual or triple boot? Only "Bootcamp" of the items you listed is a "partitioning program". rEFIt is an EFI boot manager and GRUB is a Linux bootloader.
> **joka. said:**
> 3. Which one would you suggest I use for triple booting? [Easiest to use and least amount of problems]You will likely need all three at some point. (though Bootcamp can be replaced with some other method of partitioning).
> **joka. said:**
> 4. If you can provide me with steps that would be awesome. [I know there are a few pages in the Ubuntu forums that explains it, but I found that some people ended up having problems after following those instructions. If you can provide me with the link with the least amount of problems.]
See the AppleInstallation wiki page as posted.

If you want more than 50% to go to Ubuntu and Bootcamp cannot do this for you, then you can try DiskUtility or the commandline tool diskutil. Details are in the wiki page.

---

### Post by joka. on 2009-01-05
> **cyberdork33 said:**
> If you want more than 50% to go to Ubuntu and Bootcamp cannot do this for you, then you can try DiskUtility or the commandline tool diskutil. Details are in the wiki page.

With Bootcamp, doesn't it have Window installers so that once you install Windows, all or most of things are sync? So if you use DiskUtility, wouldn't some things not work or be different? Or are Bootcamp and DiskUtility just to partition and nothing else?

I'm guessing DiskUtility is preloaded onto the Mac? On the wiki page they provided an example:
```
sudo diskutil resizeVolume disk0s2 200G
```
I'm a bit confused as to how to use DiskUtility. What's the difference between DiskUtility and Bootcamp? Would it be resizing the partition after you made the partitions... so you would be using that code in Linux?

If someone can provide me with a link to triple booting using DiskUtility or another partitioning program besides Bootcamp that would be great. I want more than 50% of the hard drive to go to Windows and Linux and to make OS X as small as possible [and apparently Bootcamp can't do this].

---

### Post by cyberdork33 on 2009-01-06
> **joka. said:**
> With Bootcamp, doesn't it have Window installers so that once you install Windows, all or most of things are sync?
The drivers are located on the Leopard Installation DVD that you get with your mac.

> **joka. said:**
> So if you use DiskUtility, wouldn't some things not work or be different? Or are Bootcamp and DiskUtility just to partition and nothing else?The BootCamp assistant really just helps you create a partition for Windows. That's it. Your Leopard DVD has the windows drivers on it.

> **joka. said:**
> I'm guessing DiskUtility is preloaded onto the Mac? On the wiki page they provided an example:
```
sudo diskutil resizeVolume disk0s2 200G
```I'm a bit confused as to how to use DiskUtility. What's the difference between DiskUtility and Bootcamp? Would it be resizing the partition after you made the partitions... so you would be using that code in Linux?
Disk Utility is the partioning app that comes with OSX. It is located in Applications > Utilities > Disk Utility

diskutil is a commandline utility to do the same things that Disk Utility can do (and more). The Bootcamp assistant and Disk Utility both use this 'diskutil' utlity to actually do the partitioning, but they are much prettier.

The usage of diskutil is explained just above that code. disk0s2 is your OSX partition (the second partition on the primary disk). and the 200G means that you want to resize the indicated partition to 200GB. So if your whole hard drive is 350GB, and you wanted OSX to take approximately 50% of that, you would do:
```
sudo diskutil resizeVolume disk0s2 175G
```

> **joka. said:**
> If someone can provide me with a link to triple booting using DiskUtility or another partitioning program besides Bootcamp that would be great. I want more than 50% of the hard drive to go to Windows and Linux and to make OS X as small as possible [and apparently Bootcamp can't do this].
The guide to triple boot is in the link i provided. Please read through it. You should follow that procedure. If you having a problem with any particular, specific part of that guide, then please ask.
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

---

### Post by joka. on 2009-01-07
Thank you cyberdork33. You've been very helpful and patient with my stupid questions.

I'll probably get my MBP 5,1 2.53ghz [was about to get the 2.8ghz w/ 7200 rmp hard drive but very expensive after tax and needs to be custom made and shipped] this weekend. I'll make a new post on how things go and if there are any problems once I get everything set up. In the mean while I'll just read related posts from other people unless I come up with last min. questions.

---

### Post by emmary on 2009-01-07
You have a nice Apple laptop? Then this is a perfect laptop charger for Apple series. Have your power and enjoy the ultra entertainment.Have it now and you won't miss it.


Tradestead has been growing rapidly since it was founded in 2004. It is a leading supplier of consumer electronics, IT facilities and accessories direct from China. What makes Tradestead different is that customers can easily order online thanks to the cutting-edge B2B E-commerce platform at [www.tradestead.com](www.tradestead.com). Furthermore, customers can enjoy flexible payment options, such as wired transfer (T/T), major credit cards, PayPal, Western Union, and Letter of Credit (L/C), and various shipping choices as you like, including Express Couriers (FedEx, DHL, UPS and TNT), Air Freight, Ocean Freight, EMS, and Postal Parcel. It is noticeable that customers can use their own couriers. Plus, the responsible customer service team helps keep customer loyalty.

---

### Post by cyberdork33 on 2009-01-07
> **joka. said:**
> Thank you cyberdork33. You've been very helpful and patient with my stupid questions.

I'll probably get my MBP 5,1 2.53ghz [was about to get the 2.8ghz w/ 7200 rmp hard drive but very expensive after tax and needs to be custom made and shipped] this weekend. I'll make a new post on how things go and if there are any problems once I get everything set up. In the mean while I'll just read related posts from other people unless I come up with last min. questions.
It may be much cheaper to purchase your own hard drive and replace it yourself. Apple made this much easier in the new MacbookPro.

---

### Post by joka. on 2009-01-07
> **cyberdork33 said:**
> It may be much cheaper to purchase your own hard drive and replace it yourself. Apple made this much easier in the new MacbookPro.

Yep, that's very true.

A question actually popped into my head while thinking about partitioning. In the near future [1-2 years] Windows is coming out with Windows 7. Now I know that to triple boot on a Mac, you have to do it in a specific order or way in order for it to be able to boot all of the OS properly. Say if I installed Windows Vista now and decided to install Windows 7 when it comes out, but instead of doing the upgrade I delete Windows Vista from the hard drive and wipe that partition slate clean to install Windows 7, would that cause any problems or would I have to install Linux again with it? Another thing is if I choose to delete either Windows or Linux from the hard drive [if I don't feel I have a need for it anymore] after doing the triple boot, would that cause any problems with booting into the OS or resizing the partition?

---

### Post by pxwpxw on 2009-01-07
> **joka. said:**
> Yep, that's very true.

A question actually popped into my head while thinking about partitioning. In the near future [1-2 years] Windows is coming out with Windows 7. Now I know that to triple boot on a Mac, you have to do it in a specific order or way in order for it to be able to boot all of the OS properly. 

OK so far
> 
Say if I installed Windows Vista now and decided to install Windows 7 when it comes out, but instead of doing the upgrade I delete Windows Vista from the hard drive and wipe that partition slate clean to install Windows 7, would that cause any problems or would I have to install Linux again with it? 

Probably. If you wanted to do anything as drastic with an unknown Windows7, it would probably be best to wipe the whole disk and start again - the moral is to keep backups. A complete re install does not take too long and is usually better than struggling with unknown problems.
Windows installers tend to interfere with other installations, sometimes without warning.
> 
Another thing is if I choose to delete either Windows or Linux from the hard drive [if I don't feel I have a need for it anymore] after doing the triple boot, would that cause any problems with booting into the OS or resizing the partition?

When you make changes to partition structure, this can affect linux bootlaoder configuration and MS windows booting, but does not normally affect MacOSX, and you can always use the MacOSX install DVD and the ubuntu Desktop CD for rescue opertations.

You use rEFIt (in MacOSX) to fix MBR sync  bootloader rpblems caused by the ubuntu gparted partitioner

But is best to avoid partition changes except where really necessary.

In any case, backups (Time Machine) and keeping a record of what is installed on which partition, and what you are planning to change, is the best insurance.

---

### Post by joka. on 2009-01-07
Ok, I was in Best Buy earlier and played with the MBP's there. The Macs there aren't loaded with a lot of programs unlike at the Apple store where they loaded a lot of programs for you to test out. I was actually able to partition the hard drive more than 50% using Bootcamp. Bootcamp can make any size partiton you want except you must leave 5GB extra space free for the OS X. As long as you didn't install a lot of programs [like in the Apple store], you're able to have more freedom in the size of the partitions. I guess the people working in the Apple store didn't really know what they were talking about [or at least the sales person I talked to]... or perhaps I didn't state my question clear enough.

---

### Post by pxwpxw on 2009-01-07
> **joka. said:**
> Ok, I was in Best Buy earlier and played with the MBP's there. The Macs there aren't loaded with a lot of programs unlike at the Apple store where they loaded a lot of programs for you to test out. I was actually able to partition the hard drive more than 50% using Bootcamp. Bootcamp can make any size partiton you want except you must leave 5GB extra space free for the OS X. As long as you didn't install a lot of programs [like in the Apple store], you're able to have more freedom in the size of the partitions. I guess the people working in the Apple store didn't really know what they were talking about [or at least the sales person I talked to]... or perhaps I didn't state my question clear enough.

That is a useful bit of info about the bootcamp slider going below 50%.
I could not help there as I don't have Leopard just yet.
Nothing beats checking for yourself, hands on experience.

---

### Post by cyberdork33 on 2009-01-08
There is also the added possibility that Windows 7 will support booting from EFI in which case it shouldn't matter ;)

---

### Post by joka. on 2009-01-09
Hey, I just realized I don't really know what EFI is or what it does. Can you explain it to me? I've been hearing it a lot so I kinda just went with it sorta knowing. :neutral:

---

### Post by cyberdork33 on 2009-01-09
> **joka. said:**
> Hey, I just realized I don't really know what EFI is or what it does. Can you explain it to me? I've been hearing it a lot so I kinda just went with it sorta knowing. :neutral:
as a generic answer "Extensible Firmware Interface", it is like the BIOS on a PC. for more info see:
[http://en.wikipedia.org/wiki/Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Extensible_Firmware_Interface)
[http://www.uefi.org/](http://www.uefi.org/)

---

