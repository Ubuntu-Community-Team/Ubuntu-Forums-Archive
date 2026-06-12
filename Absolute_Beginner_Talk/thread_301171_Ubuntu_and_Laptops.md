---
title: "Ubuntu and Laptops"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by Foustus on 2006-11-16
hey everyone I dont know if this is the right area, but I am having trouble with my new laptop. I want to run ubuntu but I cant get it to install. Is there a special version for laptops. I tried Edgy eft but that just froze up the machine. I tried Breezy Badger and that sort of worked but once installed, I am unable to connect to Internet. Can someone help thanks

---

### Post by fritz_monroe on 2006-11-16
I'm running Dapper Drake just fine on my Sony VAIO.  Been working great for about a year now.  Post the specs of your laptop and the folks here might be able to assist a little more.

I'm assuming that the part that you can't get working is the wireless?

Do you have an option to connect a network cable to the laptop?  If so, see if you can get online via the network card.  At least that will show that everything else is working.

---

### Post by meng on 2006-11-16
Try the alternate CD install. Also would wonder if your burn is bad, perhaps reburning at a lower speed would help. There is no special version for laptops, in fact the standard version includes PCMCIA support, power management, etc.

---

### Post by nickpaton on 2006-11-16
Hi

We need more information.
Please would you tell us the make & model of the laptop.
How much memory?
CPU?
Graphics card?

Regardless of whether the lappy is 64bit, I suggest that you install 32bit Dapper 6.06 x86 desktop.

---

### Post by GenX on 2006-11-16
OK so I am sort of in the same boat. I am trying to install Edgy on a new Maxtor 100gb external drive that I wish to us strictly for Linux. I can get most of the way through the install until I get to the partitioning segment. I select the options that lets Edgy auto partition my drive, and click forward. The section comes up next as to determine the partition size you prefer(which is set for 50% default) and I click forward without adjusting anything. Then the icon goes into busy mode and never stops. I see no evidence of any activity happening what so ever except for the mouse busy icon.

I am running a HP pavilion ZD8000 modified to these specs:
Windows XP Home Sp2
Intel P4 3.2 ghz 64bit HT chip
1 gig ram
80 gb hard drive
ATI Radeon X300

The drive I want to install to is:
Maxtor 3200 USB
100gb/93.2 Free
I am currently reformatting to be sure the factory format was clean.

I am going to try to write a new CD to install from using the lowest setting possible. The last CD write I tried was at 4x. 

The Live cd works great so I have no clue as to what why it won't activate the installation.

---

### Post by rlozano on 2006-11-16
things should work perfectly. you have a very nice laptop specs. HT by default is turned off in ubuntu.

see this thread: [http://ubuntuforums.org/showthread.php?p=895077](http://ubuntuforums.org/showthread.php?p=895077)

GenX, maybe you can try to fdisk your maxtor before using it to linux.

thanks and hope this helps.

---

### Post by GenX on 2006-11-16
> **rlozano said:**
> things should work perfectly. you have a very nice laptop specs. HT by default is turned off in ubuntu.

see this thread: [http://ubuntuforums.org/showthread.php?p=895077](http://ubuntuforums.org/showthread.php?p=895077)

GenX, maybe you can try to fdisk your maxtor before using it to linux.

thanks and hope this helps.
Thank you very much. I have bookmarked the Hyperthreading activation post to try it when I get Linux to boot from the Hard drive.

I am not sure what fdisk is. The hard drive is formatted to NTFS. Is this right if I am only using it for Linux?

---

### Post by Foustus on 2006-11-16
My laptop is an Everex. I think its an off brand. Anyway here are the specs.

VIA/S3G UniChrome Pro IGP: Display Adapter
Fujitsu MHV2040BH: Disk Drive
Philips CDRW/DVD SCB526565: DVD/CD-ROM drives
Broadcom 802.11g Network Adapter
VIA Rhine II Fast Ethernet Adapter
Generic CardBus Controller: PCMCIA Adapter
Intel Celeron M Processor 1.30 GHz

Thanks everyone

> **nickpaton said:**
> Hi

We need more information.
Please would you tell us the make & model of the laptop.
How much memory?
CPU?
Graphics card?

Regardless of whether the lappy is 64bit, I suggest that you install 32bit Dapper 6.06 x86 desktop.

---

### Post by rlozano on 2006-11-16
> **GenX said:**
> I am not sure what fdisk is. The hard drive is formatted to NTFS. Is this right if I am only using it for Linux?

i'ts a utility even in windows you can find. something like low level formatting. but actually, even if your drive is in NTFS, there should not be a problem when you install linux. but no harm in trying....

```
My laptop is an Everex. I think its an off brand. Anyway here are the specs.

VIA/S3G UniChrome Pro IGP: Display Adapter
Fujitsu MHV2040BH: Disk Drive
Philips CDRW/DVD SCB526565: DVD/CD-ROM drives
Broadcom 802.11g Network Adapter
VIA Rhine II Fast Ethernet Adapter
Generic CardBus Controller: PCMCIA Adapter
Intel Celeron M Processor 1.30 GHz
```

i dont see any problem here, except that of the Ethernet adapter. or maybe im the only one not really familiar with the make and the brand.

but is it working on Live CD?

---

### Post by Foustus on 2006-11-16
I have Edgy eft on my PC and everything went fine. But when I put it into my laptop it takes forever just to get to the desktop. Once there I am unable to do any thing. I try to click on the install Icon but when I do everything freezes up

> **rlozano said:**
> i'ts a utility even in windows you can find. something like low level formatting. but actually, even if your drive is in NTFS, there should not be a problem when you install linux. but no harm in trying....

```
My laptop is an Everex. I think its an off brand. Anyway here are the specs.

VIA/S3G UniChrome Pro IGP: Display Adapter
Fujitsu MHV2040BH: Disk Drive
Philips CDRW/DVD SCB526565: DVD/CD-ROM drives
Broadcom 802.11g Network Adapter
VIA Rhine II Fast Ethernet Adapter
Generic CardBus Controller: PCMCIA Adapter
Intel Celeron M Processor 1.30 GHz
```

i dont see any problem here, except that of the Ethernet adapter. or maybe im the only one not really familiar with the make and the brand.

but is it working on Live CD?

---

### Post by GenX on 2006-11-16
> **GenX said:**
> OK so I am sort of in the same boat. I am trying to install Edgy on a new Maxtor 100gb external drive that I wish to us strictly for Linux. I can get most of the way through the install until I get to the partitioning segment. I select the options that lets Edgy auto partition my drive, and click forward. The section comes up next as to determine the partition size you prefer(which is set for 50% default) and I click forward without adjusting anything. Then the icon goes into busy mode and never stops. I see no evidence of any activity happening what so ever except for the mouse busy icon.

I am running a HP pavilion ZD8000 modified to these specs:
Windows XP Home Sp2
Intel P4 3.2 ghz 64bit HT chip
1 gig ram
80 gb hard drive
ATI Radeon X300

The drive I want to install to is:
Maxtor 3200 USB
100gb/93.2 Free
I am currently reformatting to be sure the factory format was clean.

I am going to try to write a new CD to install from using the lowest setting possible. The last CD write I tried was at 4x. 

The Live cd works great so I have no clue as to what why it won't activate the installation.

Well I went back and did a couple of things. Something went right because I am running the Ubuntu from my external hard drive now. I did 3 things before trying the install again, but I didn't do them one by one interspaced w/ the install so I am unsure which of the following things worked:

1. First I reformatted the drive in XP. It was reformatted in NTFS.
2. I burned another copy of Ubuntu to cd writing at 1x.
3. Under the partition manager in Ubuntu I unmounted my external drive. It had a lock icon listed next to it before the unmounting and it disappeared after wards. I have no idea what so ever what unmounting is or does, but I did it.

I was going to activate hyperthreading, but it says that it makes the distro insecure by enabling one thread to access another and I don't think I care to have that. Ubuntu blazez on this box even without the HT so there ya go.

---

### Post by nickpaton on 2006-11-17
> **Foustus said:**
> My laptop is an Everex. I think its an off brand. Anyway here are the specs.

VIA/S3G UniChrome Pro IGP: Display Adapter
Fujitsu MHV2040BH: Disk Drive
Philips CDRW/DVD SCB526565: DVD/CD-ROM drives
Broadcom 802.11g Network Adapter
VIA Rhine II Fast Ethernet Adapter
Generic CardBus Controller: PCMCIA Adapter
Intel Celeron M Processor 1.30 GHz

Thanks everyone

@Foustus - As has been said before everything looks OK & I believe the VIA Rhine II adapter is also OK.

_IMPORTANT_: Please would you say how much memory you have.  

(On one box I could not get Edge to load with 256Mb and had to take it up to 512Mb.)

For information for anyone else the HDD is SATA 40Gb.

I'm right in thinking that you want to remove XP entirely and replace with Edgy.

I don't know much about SATA installation, but I've read one or two posts and you may be better off using Dapper 6.06 rather than Edge 6.10 which is more cutting edge and by inference can cause problems in certain areas.  
It may be that SATA and Edge are OK and someone may be able to confirm this.

Regarding starting with a "new" HDD, and continuing with Edgy for the time being....

1. It is vitally important that you check your install CD by using "Check CD For Defects" option on the initial choices menu.  If it fails that, then there is no point in proceding further and you need to check the md5 checksum on your original download.
It could also be that, as GenX has said, that you have burnt your CD too fast, so try burning it much, much slower.
Any problems here get back to us.

2. After you have checked the CD and it has passed, you need to reboot and once again get to the choices menu.  Press F6 key (Other Options) and you will see a line of text towards  the right hand corner.  Simply type:

```
noapic nolapic
```

You may not see it, but it adds text to the end of that line.

In Dapper, certainly, It really speeds up loading and general running of the distro, but this may have been sorted in Edgy.  Doesn't do any harm AFAIK!

For more information about what this does, see:

[http://www.ubuntuforums.org/showthread.php?t=228499]("http://www.ubuntuforums.org/showthread.php?t=228499")

3. Patitioning - I can't go into my system to give detailed instructions, but I always do it manually so I know what I have.
So if the laptop is only to be used for Edgy, for a 40Gb disc I would suggest:

Ext3: 10Gb
Swap: Twice the size of your memory
FAT32: The rest.  I always have such a partition where I store all my files etc, just incase I need to reload Ubuntu.  With the separate FAT32 partition I would not therefore lose all my saved data.

Get back with how you are getting on.
HTH!

---

### Post by gn2 on 2006-11-17
> **GenX said:**
> OK so I am sort of in the same boat. I am trying to install Edgy on a new Maxtor 100gb external drive that I wish to us strictly for Linux. 

Have you tried PCLinuxOS?

It has the option of installing to USB as an option during the install process. 

I've used this option and found it to be very simple and straightforward.

---

### Post by Foustus on 2006-11-17
What do you mean by alternate CD install? I just burned Dapper. When the CD is inserted in the drive and the laptop is rebooted, the first option that I have is start or install. When I select that option I am taken directly to the desktop which takes forever. Is there anyway to just begin installing and bypass the live CD thing?

> **meng said:**
> Try the alternate CD install. Also would wonder if your burn is bad, perhaps reburning at a lower speed would help. There is no special version for laptops, in fact the standard version includes PCMCIA support, power management, etc.

---

### Post by Foustus on 2006-11-17
Okay. CD burned at 4x. tried downloading Dapper from Ubuntu website. Having the same trouble as Edgy. I am convinced that if there is a way to install directly, then there would not be a problem. Is there a way to bypass the live cd portion and just simply install? I am able to install Breezy and with the exeption of DHCP error it works fine. Once installed I am unable to connect to Internet through my ethernet connection or my wireless connection. 


> **nickpaton said:**
> @Foustus - As has been said before everything looks OK & I believe the VIA Rhine II adapter is also OK.

_IMPORTANT_: Please would you say how much memory you have.  

(On one box I could not get Edge to load with 256Mb and had to take it up to 512Mb.)

For information for anyone else the HDD is SATA 40Gb.

I'm right in thinking that you want to remove XP entirely and replace with Edgy.

I don't know much about SATA installation, but I've read one or two posts and you may be better off using Dapper 6.06 rather than Edge 6.10 which is more cutting edge and by inference can cause problems in certain areas.  
It may be that SATA and Edge are OK and someone may be able to confirm this.

Regarding starting with a "new" HDD, and continuing with Edgy for the time being....

1. It is vitally important that you check your install CD by using "Check CD For Defects" option on the initial choices menu.  If it fails that, then there is no point in proceding further and you need to check the md5 checksum on your original download.
It could also be that, as GenX has said, that you have burnt your CD too fast, so try burning it much, much slower.
Any problems here get back to us.

2. After you have checked the CD and it has passed, you need to reboot and once again get to the choices menu.  Press F6 key (Other Options) and you will see a line of text towards  the right hand corner.  Simply type:

```
noapic nolapic
```

You may not see it, but it adds text to the end of that line.

In Dapper, certainly, It really speeds up loading and general running of the distro, but this may have been sorted in Edgy.  Doesn't do any harm AFAIK!

For more information about what this does, see:

[http://www.ubuntuforums.org/showthread.php?t=228499]("http://www.ubuntuforums.org/showthread.php?t=228499")

3. Patitioning - I can't go into my system to give detailed instructions, but I always do it manually so I know what I have.
So if the laptop is only to be used for Edgy, for a 40Gb disc I would suggest:

Ext3: 10Gb
Swap: Twice the size of your memory
FAT32: The rest.  I always have such a partition where I store all my files etc, just incase I need to reload Ubuntu.  With the separate FAT32 partition I would not therefore lose all my saved data.

Get back with how you are getting on.
HTH!

---

### Post by Foustus on 2006-11-17
CD checks out fine 0 checksum errors.



> **Foustus said:**
> Okay. CD burned at 4x. tried downloading Dapper from Ubuntu website. Having the same trouble as Edgy. I am convinced that if there is a way to install directly, then there would not be a problem. Is there a way to bypass the live cd portion and just simply install? I am able to install Breezy and with the exeption of DHCP error it works fine. Once installed I am unable to connect to Internet through my ethernet connection or my wireless connection.

---

### Post by Foustus on 2006-11-17
tried the noapic nolapic thing. just made it far worse. goes much slower


> **Foustus said:**
> Okay. CD burned at 4x. tried downloading Dapper from Ubuntu website. Having the same trouble as Edgy. I am convinced that if there is a way to install directly, then there would not be a problem. Is there a way to bypass the live cd portion and just simply install? I am able to install Breezy and with the exeption of DHCP error it works fine. Once installed I am unable to connect to Internet through my ethernet connection or my wireless connection.

---

### Post by nickpaton on 2006-11-17
Mmmm

You haven't answered as to how much memory is fitted to the laptop.  Less than 256Mb, and Ubuntu will not run.
Please answer that.:) 

"Problem" could be that you have a SATA...I'll do some digging around.

---

### Post by nickpaton on 2006-11-17
Foustus

I'd be wasting your time if I kept you waiting for a reply from me, since I don't know a lot about Sata.

Make a new post in beginners section titled somwthing like "Problems loading Dapper and Edgy on SATA"

Post ALL laptop information including MEMORY (!!)

Post briefly the problems you have been having, including noapic nolapic (which could be wrong for SATA anyway for which I apologise BTW).

There will be people out there who can help you, and I'll be interested to see what the fix is.

Sorry to waste your time M8 & good luck - just persevere!

---

### Post by Foustus on 2006-11-17
192 MB
I can get Breezy baddger to run perfectly but once installed I am unable to connect to the internet at all.

> **nickpaton said:**
> Mmmm

You haven't answered as to how much memory is fitted to the laptop.  Less than 256Mb, and Ubuntu will not run.
Please answer that.:) 

"Problem" could be that you have a SATA...I'll do some digging around.

---

### Post by Bachstelze on 2006-11-17
Please give more details. How do you connect to the Net ? Also paste the output of *sudo ifconfig -a* so we can see if your NIC was detected properly.

---

### Post by nickpaton on 2006-11-17
Double post

---

### Post by nickpaton on 2006-11-17
And also include

```
sudo lshw -C network
```

Note lower case L (lshw) and upper case c (C)

which will give detected network hardware.

BTW 192Mb is not enough recommended memory to run Dapper or Edgy.

---

### Post by Mimsy on 2006-11-17
> **Foustus said:**
> 192 MB

That would be a part of your problem; 192 MB is not enough to run Ubuntu Dapper from a live CD. Have you tried Xubuntu? It is less memory intensive. It still won't be very fast from a live CD though.

/Mimsy

---

### Post by GenX on 2006-11-17
> **gn2 said:**
> Have you tried PCLinuxOS?

It has the option of installing to USB as an option during the install process. 

I've used this option and found it to be very simple and straightforward.

I have my issues worked out. I had to dedicate the whole 100gb drive to it because I did not understand the partitioning. So maybe I can go back and alter it later. The only problem I have now is getting a radio stream to play through a media player.

---

### Post by Foustus on 2006-11-17
Yes tried xubuntu, I seem to have video problem. When I open Firefox, and scoll there is alot of lag. In other words when I use the scroll bar to move up and down the page there is alot of delay and the screen is very wavy. I think maybe I will just give up and reinstall Windows :( 



> **Mimsy said:**
> That would be a part of your problem; 192 MB is not enough to run Ubuntu Dapper from a live CD. Have you tried Xubuntu? It is less memory intensive. It still won't be very fast from a live CD though.

/Mimsy

---

### Post by Foustus on 2006-11-17
If you want to see specs on my laptop see page 1 of this thread:( 

> **Foustus said:**
> Yes tried xubuntu, I seem to have video problem. When I open Firefox, and scoll there is alot of lag. In other words when I use the scroll bar to move up and down the page there is alot of delay and the screen is very wavy. I think maybe I will just give up and reinstall Windows :(

---

### Post by Mimsy on 2006-11-17
Lag is not necessarily a video card problem. Are you running from the live CD when you get it? If that is the case, the lag will probably go away once you run Xunbuntu installed from your hard drive.

I was in that situation with Ubuntu on my laptop.

/Mimsy

---

### Post by Foustus on 2006-11-17
this lag is after xubuntu is fully installed

> **Mimsy said:**
> Lag is not necessarily a video card problem. Are you running from the live CD when you get it? If that is the case, the lag will probably go away once you run Xunbuntu installed from your hard drive.

I was in that situation with Ubuntu on my laptop.

/Mimsy

---

### Post by Foustus on 2006-11-17
Also I do not know how to configure my wireless connection

> **Mimsy said:**
> Lag is not necessarily a video card problem. Are you running from the live CD when you get it? If that is the case, the lag will probably go away once you run Xunbuntu installed from your hard drive.

I was in that situation with Ubuntu on my laptop.

/Mimsy

---

### Post by lyceum on 2006-11-17
1. Broadcom does not work well (or at all) with Linux. You would need to get a new wireless/ethernet card.

2. upgrade your memory. I would recoment 512mbs. 

3. If edgy is not working get dapper.

4. If you do not wat to upgrade the memory try fluxbuntu.

fluxbuntu.com

Good luck!

---

### Post by Mimsy on 2006-11-17
512MB would be the ideal. If you're poor or cheap (I am both! :) ) you can run Ubuntu on 256 MB, but it won't fly and be all cool nice and flashy, like it will on 512 MB.

/Mimsy

---

### Post by nickpaton on 2006-11-17
> **lyceum said:**
> Broadcom does not work well (or at all) with Linux. You would need to get a new wireless/ethernet card.

Since when does Broadcom not work?  I'm currently typing this on a broadcom-based-wireless-chip laptop, and on both Dapper and Edgy didn't have too many problems.
There are loads of really good simple broadcom HOWTO's which work!

---

### Post by Foustus on 2006-11-17
Could you point me in the right direction, keeping in mind that I am ***_completely_***ignorant toward the whole wireless thing:confused:  



> **nickpaton said:**
> Since when does Broadcom not work?  I'm currently typing this on a broadcom-based-wireless-chip laptop, and on both Dapper and Edgy didn't have too many problems.
There are loads of really good simple broadcom HOWTO's which work!

---

### Post by ahaslam on 2006-11-17
> **Foustus said:**
> My laptop is an Everex. I think its an off brand. Anyway here are the specs.

VIA/S3G UniChrome Pro IGP: Display Adapter
Fujitsu MHV2040BH: Disk Drive
Philips CDRW/DVD SCB526565: DVD/CD-ROM drives
Broadcom 802.11g Network Adapter
VIA Rhine II Fast Ethernet Adapter
Generic CardBus Controller: PCMCIA Adapter
Intel Celeron M Processor 1.30 GHz

Thanks everyone

I have a similarly spec'd laptop with the dreaded Unichrome pro graphics. I don't recommend Edgy as battery life isn't as good for me. I also wouldn't recommend Breezy, as I couldn't get hardware acceleration for the graphics. Dapper however works perfectly for me. If you've had problem installing, I recommend the 'alternative' Dapper installation. 

Tony.

PS. I didn't read the entire post, so I apologise for any repetition.

---

### Post by nickpaton on 2006-11-17
> **Foustus said:**
> Could you point me in the right direction, keeping in mind that I am ***_completely_***ignorant toward the whole wireless thing:confused:

To answer this  I still need the answer to:

```
sudo lshw -C network
```

Note lower case L (lshw) and upper case c (C)

We **MUST** know this, since there are different Broadcom chips and slightly different ways of doing it.

BUT, what is more important is getting the distro installed in the first place; we can then move onto wireless etc.

It all looks like somewhat bad news for you, but it's not really.  You will get a good virus free stable system, but it takes a little bit of perserverence in the first week or two.

In summary, it seems you need more memory, to take you up to at least 256Mb and preferably higher.
You need to try what is called Alternative Dapper - yup another CD download but short term pain, long term gain.
The wireless and any other issues we will get resolved as they appear.

Good luck M8

---

### Post by Foustus on 2006-11-17
What is the alternative install. I have downloaded Dapper but It just simply wont install from a live CD

> **Anthony Haslam said:**
> I have a similarly spec'd laptop with the dreaded Unichrome pro graphics. I don't recommend Edgy as battery life isn't as good for me. I also wouldn't recommend Breezy, as I couldn't get hardware acceleration for the graphics. Dapper however works perfectly for me. If you've had problem installing, I recommend the 'alternative' Dapper installation. 

Tony.

PS. I didn't read the entire post, so I apologise for any repetition.

---

### Post by Foustus on 2006-11-17
Yes I will get that for you. It might be an hour or so I am going to try the alternate dapper CD and see if I have better luck

> **nickpaton said:**
> To answer this  I still need the answer to:

```
sudo lshw -C network
```

Note lower case L (lshw) and upper case c (C)

We **MUST** know this, since there are different Broadcom chips and slightly different ways of doing it.

BUT, what is more important is getting the distro installed in the first place; we can then move onto wireless etc.

It all looks like somewhat bad news for you, but it's not really.  You will get a good virus free stable system, but it takes a little bit of perserverence in the first week or two.

In summary, it seems you need more memory, to take you up to at least 256Mb and preferably higher.
You need to try what is called Alternative Dapper - yup another CD download but short term pain, long term gain.
The wireless and any other issues we will get resolved as they appear.

Good luck M8

---

### Post by nickpaton on 2006-11-17
Sorry Foustus - we're not answering YOUR questions either!! LOL

Alternative Dapper:

What ts actually is:

> The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:

    * creating pre-configured OEM systems;
    * setting up automated deployments;
    * upgrading from older installations without network access;
    * LVM and/or RAID partitioning;
    * installing GRUB to a location other than the Master Boot Record;
    * installs on systems with less than about 192MB of RAM. 


It's really used for older PC's and works if nothing else will.

Go to the main 6.06 download page:

[http://www.ubuntu.com/products/GetUbuntu/download#lts]("http://www.ubuntu.com/products/GetUbuntu/download#lts")

Select the country you are nearest to, to download the mirror.

Then on that page scroll down to find and download the Alternative CD download for x86 desktop.

Good luck M8

---

### Post by lyceum on 2006-11-17
> **nickpaton said:**
> Since when does Broadcom not work?  I'm currently typing this on a broadcom-based-wireless-chip laptop, and on both Dapper and Edgy didn't have too many problems.
There are loads of really good simple broadcom HOWTO's which work!

Okay, it doesn't "just work" and even w/ the how too's, I could not get mine to work. The light came on, but no one was home so to speak.

---

### Post by Foustus on 2006-11-17
Okay here you are. The first is my wireless adapter. Seems to bedisabled for some reason.


foustus@SATANUS2:~$ sudo lshw -C network
Password:
  *-network:0 DISABLED
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@00:06.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:5a:06:d6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.15-27-386 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:d0000000-d0001fff irq:201
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 78
       serial: 00:40:ca:dd:0b:0d
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=via-rhine driverversion=1.2.0-2.6 duplex=full ip=68.99.21.75 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:2000-20ff iomemory:d0002400-d00024ff irq:209
foustus@SATANUS2:~$





> **nickpaton said:**
> To answer this  I still need the answer to:

```
sudo lshw -C network
```

Note lower case L (lshw) and upper case c (C)

We **MUST** know this, since there are different Broadcom chips and slightly different ways of doing it.

BUT, what is more important is getting the distro installed in the first place; we can then move onto wireless etc.

It all looks like somewhat bad news for you, but it's not really.  You will get a good virus free stable system, but it takes a little bit of perserverence in the first week or two.

In summary, it seems you need more memory, to take you up to at least 256Mb and preferably higher.
You need to try what is called Alternative Dapper - yup another CD download but short term pain, long term gain.
The wireless and any other issues we will get resolved as they appear.

Good luck M8

---

### Post by nickpaton on 2006-11-18
That's fine Foustus.

The reason for running that command is to make sure that Dapper has detected the hardware, which it has.

Now we need to apply suitable software to make it run.

Run the following script:

[http://www.ubuntuforums.org/showthread.php?t=197102]("http://www.ubuntuforums.org/showthread.php?t=197102")

This is a great HOWTO which I tend to use.

You do need access to the Internet, and it looks from your Hardware output that the wired part works OK.  If you have any problems there get back.

I always have a bit of a problem getting the wireless part of the PC to be accepted, since the wired part wants all the action; so I suggest once you've got the software loaded and are into Network Manager etc., that you disconnect the LAN cable, and disable the wired connection (which may be called Eth1), and force the default connection to be your wireless one possibly Eth0.
You may also want to go into the wireless properties and add the SSID (name of your wireless connection as you will have already entered in your router), but in both your router and wireless connection initially run unencrypted.

Ok try that - I'll around from time to time - domestic chores call from the wife!!

Good luck and great to see that alternative Dapper works for ya:)

---

### Post by Foustus on 2006-11-18
BEAUTIFUL!!!!!!
Thanks to everyone for all the help in getting this set up.
This is agreat community!



> **nickpaton said:**
> That's fine Foustus.

The reason for running that command is to make sure that Dapper has detected the hardware, which it has.

Now we need to apply suitable software to make it run.

Run the following script:

[http://www.ubuntuforums.org/showthread.php?t=197102]("http://www.ubuntuforums.org/showthread.php?t=197102")

This is a great HOWTO which I tend to use.

You do need access to the Internet, and it looks from your Hardware output that the wired part works OK.  If you have any problems there get back.

I always have a bit of a problem getting the wireless part of the PC to be accepted, since the wired part wants all the action; so I suggest once you've got the software loaded and are into Network Manager etc., that you disconnect the LAN cable, and disable the wired connection (which may be called Eth1), and force the default connection to be your wireless one possibly Eth0.
You may also want to go into the wireless properties and add the SSID (name of your wireless connection as you will have already entered in your router), but in both your router and wireless connection initially run unencrypted.

Ok try that - I'll around from time to time - domestic chores call from the wife!!

Good luck and great to see that alternative Dapper works for ya:)

---

### Post by cantormath on 2006-11-18
WHat is your hardware?
AMD pentium etc.....
I suggest you try Dapper.....

---

### Post by nickpaton on 2006-11-18
> **Foustus said:**
> BEAUTIFUL!!!!!!
Thanks to everyone for all the help in getting this set up.
This is agreat community!

A pleasure and keep the questions coming:)

---

### Post by ExMachina on 2006-11-18
I have a sony vaio pcg-k13 and the wifi DIED when i started using edgy <<
It was wonderful in dapper but edgy killed it.. any idea why?

---

### Post by nickpaton on 2006-11-18
Hi Ex Machina

Can you list your network network to make sure it's detected:

```
sudo lshw -C network
```

It will also give the chipset, and we can take it from there.

---

### Post by nickpaton on 2006-11-18
For good measure can you add:

```
iwconfig
```

and 

```
ifconfig
```

---

### Post by Foustus on 2006-11-18
Okay heres one how about games?



> **nickpaton said:**
> A pleasure and keep the questions coming:)

---

### Post by nickpaton on 2006-11-18
> **Foustus said:**
> Okay heres one how about games?

Should have kept my big mouth shut - just joking!!!:) 

I'll need to get back to you since I need my bed, but it does not look good.

That particular Unichrome graphics chip is not that well developed in Dapper, but I have found this thread which goes into a lot of detail, but needs some detailed going through since it requires compiling a special kernel and some other slightly tricky work, and for me now is not the time:

[http://ubuntuforums.org/showthread.php?t=184512]("http://ubuntuforums.org/showthread.php?t=184512")

I would say that it's not really worth it, and we may end up with you having to do a reinstall afterwards, but that's the way to learn!

it's up to you M8.  I'll do my best to help, but it's coming close to being outside of my present knowledge too.

---

### Post by mthakur2006 on 2006-11-24
Whats the problem? I have edgy running on this: (see my sig) :-D :-D

---

### Post by nickpaton on 2006-11-24
> **mthakur2006 said:**
> Whats the problem? I have edgy running on this: (see my sig) :-D :-D
Brilliant and well done M8!

---

### Post by Bachstelze on 2006-11-24
Next step : install Slackware :D

---

### Post by ScrewWindows on 2007-12-14
Hello I have repeatedly tried to install Ubuntu on my thinkpad.  It's a p2 with 288 mb ram.  I even have tried to use different hard drives.  Is there something I need to do to install on a laptop? Or is this laptop just to old? I wouldn't think it would be.  I can't even run Ubuntu off of the live cd.  My desktop works no problem with it, but not my laptop.  I also have windows 2000 on the laptop, but want to get rid of it. I hate windows! Windows causes nothing but problems, and Microsoft does not help their customers... well in my case a former customer!  On the other hard drive I tried to install it on I have windows 95.  That did not work either.  Should I reformat these drives first? I am confused, and just want to drop kick this computer!  Please help!  Thanks.

---

### Post by LaRoza on 2007-12-14
> **ScrewWindows said:**
> Hello I have repeatedly tried to install Ubuntu on my thinkpad.  It's a p2 with 288 mb ram.  I even have tried to use different hard drives.  Is there something I need to do to install on a laptop? Or is this laptop just to old? I wouldn't think it would be.  I can't even run Ubuntu off of the live cd.  My desktop works no problem with it, but not my laptop.  I also have windows 2000 on the laptop, but want to get rid of it. I hate windows! Windows causes nothing but problems, and Microsoft does not help their customers... well in my case a former customer!  On the other hard drive I tried to install it on I have windows 95.  That did not work either.  Should I reformat these drives first? I am confused, and just want to drop kick this computer!  Please help!  Thanks.

That is old, but not too old. Yes, you won't be able to use the Live CD. 

Try the alternate disk (download from the same site from Ubuntu, but check the box).

You should try a lighter distro, maybe Xubuntu in this case.

It is a text based installer, but it is easy to use.

---

