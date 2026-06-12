---
title: "Multi-boot and iMac (Triple boot with Mac OS X, Ubuntu, &amp; Windows 7)"
date: 2011-05-20
forum: Apple Hardware Users
---

### Post by japboy on 2011-05-20
Hello,

I'm currently using Ubuntu on my iMac mid2010, and have an empty partition (about 500GB) to install Windows 7.
I've already installed Mac OS X, Ubuntu 11.04, and rEFIt. Now how can I install Windows 7 here? I've also tried to format the empty partition to NTFS on Ubuntu (and it worked), but Windows 7 Installer doesn't recognize the partition :(

My 1TB HDD partitions are below:

- EFI (FAT32) 200MB
- HFS+ 200GB
- Empty 500GB
- ext4 200GB (/home)
- ext4 100GB (/)
- ext2 300MB (/boot)

Do you think I can add Windows partition w/o breaking the exisiting OSX and Ubuntu partitions?
Any help would be appreciated! Thanks.

---

### Post by ishueli on 2011-06-02
Hello there,
 
You may want to click the following link and read thru installation on windows7 on iMac...
 
[http://www.simplehelp.net/2009/01/15/using-boot-camp-to-install-windows-7-on-your-mac-the-complete-walkthrough/](http://www.simplehelp.net/2009/01/15/using-boot-camp-to-install-windows-7-on-your-mac-the-complete-walkthrough/)
 
 
Hope it Helps....
 
Regards

---

### Post by japboy on 2011-06-02
> **ishueli said:**
> Hello there,
 
You may want to click the following link and read thru installation on windows7 on iMac...
 
[http://www.simplehelp.net/2009/01/15/using-boot-camp-to-install-windows-7-on-your-mac-the-complete-walkthrough/](http://www.simplehelp.net/2009/01/15/using-boot-camp-to-install-windows-7-on-your-mac-the-complete-walkthrough/)
 
 
Hope it Helps....
 
Regards

Well, Boot Camp doesn't recognize the MBR partitions (for Ubuntu) and Disk Utility on OS X also doesn't help. I had actually done backup my data and removed the Ubuntu partions, then I installed
Windows 7 and then Ubuntu. This was the simplest way.

Thanks anyway.

---

### Post by swarup on 2011-06-02
I am very seriously looking to buy an iMac-- all ready to go get it -- but I NEED to have this triple boot set up with OSX/Ubuntu/Win 7. That is the only thing holding me back. So I take extreme interest in this thread, and would be deeply appreciative if someone who has got success could write a clear HowTo. No doubt there are also many other readers who would take great interest.

@japboy: Did you buy your iMac as a dual boot with Win7 i.e. did it come with Win 7 already on it from the factory? If not, I believe they sell these machines set up with such a dual boot, don't they? And would buying it that way make it easier to set up the triple boot?
 
         Also: Did your Ubuntu 11.04 install go smoothly? Was there any specific wiki or setup guideline you used? And how is Ubuntu working now that you have it installed? Is general functionality smooth, does everything work? Are there things that don't work?

---

### Post by japboy on 2011-06-02
@swarup

I just bought iMac. Afterwards, I also bought Windows 7 DSP separately. Dual boot of Mac OS X and Windows 7 is very easy because of Boot Camp. Triple boot is bit complex although [there are many documents from Ubuntu Community]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation"). I'm not sure if I can install Windows after Ubuntu installation though. Triple boot is possible.

I think the point is;

* Get **rEFIt** and install it first of all
* Install Windows before Ubuntu or any Unix flavours
* Make sure to create Windows partition before launching the installer

That's all. Well you should read some Ubuntu Community documents related to Mac. There are plenty actually.

---

### Post by swarup on 2011-06-02
Thank you very much for the helpful tips. :)
And yes, I'm aware that the triple boot is possible and there are various things written in the wikis about it--but I want to hear from someone who actually installed it successfully. Then I'll have more confidence that yes, in reality it can be done and is being done with success. Otherwise those wikis are mostly with older macs and older versions of ubuntu. 

Googling around one can find all sorts of stories of people's difficulties trying to get these things set up. Especially triple boots. And now 11.04 people have reported many difficulties with installation-- so I am very happy to see that you got it installed.

I actually own a MBP laptop, which I have had since 2009. When I got it I installed a dual boot OSX/Ubuntu Jaunty 9.04. And I use mostly 9.04 on that computer to this day.

I am very, very interested to know: Did your 11.04 go smoothly, no problems? And does it work well: do you have sound, does the keyboard and all the keys on it work properly?

---

### Post by japboy on 2011-06-02
@swarup

At least for me, Ubunntu 11.04 64-bit works fine without any problems. Graphic acceleration by fglrx driver is automatically recognized, sound works fine with [a little optimization]("http://help.ubuntu.com/community/Intel_iMac#Sound"), Bluetooth aluminium keyboard works fine with normal set up (perhaps need wired K/B & mouse during the installation though).

One thing you should pay attention to is where to install MBR. You'd better to install it to exactly the same boot partition, otherwise you perhaps have to format your drive entirely to remove MBR.

And [Mactel repository]("https://launchpad.net/~mactel-support") is probably MUST HAVE as you know.

Good luck.

---

### Post by ishueli on 2011-06-03
I am a very new to Linux but out of sheer curiosity I decided to install Linux on my imac (21" with Snow Leopard). I already had OSX & Windows 7 on it. By reading thru GOOGLE I managed to install Linux on a newly created partition. The system works fine even the sound and wireless etc.

The only hardware problem I am having is with Bluetooth and hence cant use magicmouse with iMac. I am also struggling to install Ubuntu Restricted Extras. Mind you it was not easy installing linux as if you make a mistake or get too adventurous then it crashes and you have to reinstall again.

Good Luck

---

### Post by swarup on 2011-06-03
@japboy: Glad to hear 11.04 is working well for you, and thanks for the tips on the install. When you say:

> You'd better to install the MBR to exactly the same boot partition, otherwise... 


This sentence is not clear for me. Just where are you saying the MBR needs to be installed? And: when the ubuntu installer disk does its install, is it the default location where it wants to put it? Or, I do remember when installed 9.04 that when the installer reaches the screen where you select how the partitions will be laid out, then you had to select "advanced" and specify a special location for something. Don't remember whether that "something" was grub, or the MBR, or what. But I've heard that the 11.04 installer no longer has that "advanced" option.

So bottom line: please give some more instruction about what you did with the MBR, and which screen during the install you did it.

@ishueli: Congratulations on your success. You mention that "By reading thru GOOGLE I managed to install Linux" as the third OS in your triple boot. Can you give a link to the page you used for the install? If you found a clear guideline, then I will go ahead and buy the computer and do the same thing. Thank you :)

---

### Post by phillat5dock on 2011-12-21
> **swarup said:**
> I am very seriously looking to buy an iMac-- all ready to go get it -- but I NEED to have this triple boot set up with OSX/Ubuntu/Win 7. That is the only thing holding me back. So I take extreme interest in this thread, and would be deeply appreciative if someone who has got success could write a clear HowTo. No doubt there are also many other readers who would take great interest.

@japboy: Did you buy your iMac as a dual boot with Win7 i.e. did it come with Win 7 already on it from the factory? If not, I believe they sell these machines set up with such a dual boot, don't they? And would buying it that way make it easier to set up the triple boot?
 
         Also: Did your Ubuntu 11.04 install go smoothly? Was there any specific wiki or setup guideline you used? And how is Ubuntu working now that you have it installed? Is general functionality smooth, does everything work? Are there things that don't work?

Hi swaraup.

I HAVE installed Ubuntu 11.10 on my mid 2011 27in iMac (11,3).
I ordered my iMac with the dual core i5 processor running at 3.6 GHz with a 2TB SATA HDD and I have 12 GB ram in it.

Initially i tried Ubuntu 11.04 by using the technique mentioned [ here ]("http://anupam128.blogspot.com/2011/02/installing-dual-boot-ubuntu-1010-on.html"). This uses the Alternative installer. But later I discovered that the iMac would actually load the Live CD version of Ubuntu 11.10 "natively".
I will try to explain.
The problem is the iMac video card, which in my iMac is an ATI/AMD Radeon HD 5670. I am not sure what the latest iMacs have but it is probably slightly different. Ubuntu 11.0, and probably 10.xx, did not have video drivers that the mac would recognise. So you had to use the text based Alternative installers to see what you were doing. 11.10 Oneiric changed this so it is very much easier.

Without writing a detailed how to until I am much more au fait with Ubuntu, here is what I have found to work.

Firstly, if you want to have Windows on the mac as well as OSX then you MUST use the BootCamp utility to set up the hard drive for Windows. You can not install Windows after Ubuntu. I know; I tried. Boot camp setup installs a "hybrid" MBR on the GPT hard drive partition scheme. Mac OS X will not boot from a MBR partition table. Also the Mac OS X installer creates a "hidden" EFI partition on the drive. Apple puts nothing in this "efi" partition but it is still required.
Once the hard drive has been set up with this hybrid partition scheme you can go ahead and load Windows, and then install the required Apple boot camp drivers. These enable Windows to work such things as the video for the LCD monitor, iSight camera, keyboard, mouse etc.
Once Windows has been installed beside Mac OS X you need to resize the Mac OS X partition so you can fit Ubuntu. You can actually do this with the BootCamp utility whilst you are setting up Windows, or, as I did, use iPartition which is a gui app. There are also ways to do this using the command line diskutil, which is what BootCamp setup uses in a nice gui.

Having created space for Ubuntu you need a way of selecting it at boot time. I use [refit]("http://refit.sourceforge.net/"). 

Download the img for Ubuntu x64 from the Ubuntu website and use the Mac's disk utility to burn a live CD.

Reboot the mac with the LiveCD and install Ubuntu. When it comes to the setup part for Grub, the boot loader, you will have to select sda and Grub will load itself into the MBR.
This wipes out the boot loader for Windows, which gave me all sorts of trouble.
I found the best thing was to load the Windows DVD and go through and repair the Windows installation.
Then you have to use the LiveCD or [Boot-repair-disk]("https://sourceforge.net/p/boot-repair-cd/home/Home/") or [Super-Grub-disk]("http://www.supergrubdisk.org/super-grub2-disk/") to repair Grub so that you can boot into either Ubuntu or Windows.

After all this you should be able to boot the iMac.
First will pop up the refit boot selector. If you do nothing it will continue to boot Mac OS X.
Or you can select Ubuntu whereupon it will load grub.
If you again do nothing it will boot into Ubuntu. If you arrow down to Windows loader it will boot into Windows.

It is not exactly clean, but until Microsoft changes Windows so it can boot from a GPT partitioned disk then there is no easier alternative.
If you don't want to boot Windows, then I suspect the whole operation becomes very much easier because Ubuntu 64 bit supports booting from a GPT disk and has EFI support. Then you just need refit as the boot selector.

After writing this outline I realise just how much I have left out. I have been on a very steep learning curve since I first contemplated trying Ubuntu on my iMac. Also, the url's I inserted won't show up in the preview, so I just hope they turn up when I post this.

Good luck.

---

### Post by xptional on 2011-12-25
Please I have some questions ..

Do we need rEFIt only for triple boot  i.e. Mac OS X, Windows, Linux  ??

I am concerned to install Ubuntu 10.04 LTS on my MacBook (Mid-2007) on separate partition. I already installed Snow Leopard 10.6.8, now I want to install Ubuntu 10.04. i.e. Dual Boot , 

Do I need to install to rEFIt for dual boot also ? 

Without installing rEFIT, when I press Alt/Opt key on MacBook while starting it shows me two disks, one with Macintosh HD and other  is Windows provided Live CD Ubuntu 10.04 LTS is in DVD-CD-ROM. 

I created two partition while installing Snow Leopard. Do  I need to create third partition SWAP before inserting Ubuntu CD for installation ?? Couldn't I create SWAP partition while installing Ubuntu ? 

Last, ..  Do I need to install GRUB ? what is GRUB, what it function ? I dont know at all ....  :( :(

---

### Post by phillat5dock on 2011-12-26
> **xptional said:**
> Please I have some questions ..

Do we need rEFIt only for triple boot  i.e. Mac OS X, Windows, Linux  ??

I am concerned to install Ubuntu 10.04 LTS on my MacBook (Mid-2007) on separate partition. I already installed Snow Leopard 10.6.8, now I want to install Ubuntu 10.04. i.e. Dual Boot , 

Do I need to install to rEFIt for dual boot also ? 

Without installing rEFIT, when I press Alt/Opt key on MacBook while starting it shows me two disks, one with Macintosh HD and other  is Windows provided Live CD Ubuntu 10.04 LTS is in DVD-CD-ROM. 

I created two partition while installing Snow Leopard. Do  I need to create third partition SWAP before inserting Ubuntu CD for installation ?? Couldn't I create SWAP partition while installing Ubuntu ? 

Last, ..  Do I need to install GRUB ? what is GRUB, what it function ? I dont know at all ....  :( :(

I might be wrong, but from what I could gather reading the rEFIt pages, once you have Ubuntu installed, you should be able to disable rEFIt and switch OS's using the normal Mac startup manager ... holding down Option at boot.
You can disable rEFIt simply by renaming the EFI folder on Macintosh HD. Just add a space before the name and enter your administrator password when asked.
As for creating the swap partition, I think you can just let the Ubuntu installer do what it needs to do. Just be sure that you don't install Ubuntu over the top of Mac OS X. Mac OS X should be on sda2 (sda1 is the EFI partition on the Hard disk and is mandatory to install Mac OS X, although it is not used for Mac OS X).  Ubuntu will create two or three extra partitions. If you use the 64 bit version of Ubuntu 11.10 it might even install an EFI version of grub. I haven't been able to do this myself though, because Windows 7 must have an MBR.

"Without installing rEFIT, when I press Alt/Opt key on MacBook while starting it shows me two disks, one with Macintosh HD and other  is Windows provided Live CD Ubuntu 10.04 LTS is in DVD-CD-ROM. " If you have installed Ubuntu, Mac OS X sees it as Windows apparently, that is if you choose not to install rEFIt. You definitely need rEFIt to triple boot. I can not find a way of not going through a chain loader with my triple boot.

---

