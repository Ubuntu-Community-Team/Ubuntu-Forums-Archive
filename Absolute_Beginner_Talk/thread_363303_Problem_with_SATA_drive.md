---
title: "Problem with SATA drive"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by mskobier on 2007-02-16
Hello,
    I am a complete noob when it comes to Linux. I have been messing around computers since 1979, so this should not be that hard. I am doing a clean install of Ubuntu 6.06LTS and have hit a definate snag. First the system. This is an AMD64 3000 with 1gig ram on a ASUS A8V-VM with integrated graphics, a 300gig Seagate SATA drive using the onboard VIA southbridge controller(VT8251). I have been trying for several days to get the install to recognize the SATA drive. I have read every post I could find and everyone seems to be runnig multiple drives as RAID or dual booting with Windows. All I want to do is install a single SATA drive and only one operating system(Ubuntu). Everything works fine until I try to install the system to the hard drive. Every thing seem to be progressing until it starts trying to identify and partion the drive. At this point the system hangs with the busy pointer just sitting there. I have left it set for an extended period of time(hours) and it never recovers. I have ran several different disk diagnostic programs as well as set the drive up in a windows based environment and all shows good. I am not afraid of entering things at the command line, but I have not been able to figure out what to enter or even where to enter it. I did read in the help files of version 6.10 64bit during initial boot, that there are parameters that I can specify and they are listed in the kernel-paramemeter.txt file, but I can not even locate that file.  I feel pretty stupid at this point. I would imagine this is not the first time this issue has surfaced, but I have been unable to locate a soultion. Any and all help would be greatly appreciated.

Thanks
Mitch

---

### Post by Spike-X on 2007-02-17
Bumping this in the hope that somebody can help him out.

Mate, I couldn't even get Windows to install onto a SATA HD. Sorry.

---

### Post by meborc on 2007-02-17
i would try to install edgy (ubuntu 6.10)... the newer kernel should help with the sata problem... edgy is a stable release... just not the LTS release... so there should be no complications... newer ubuntu means newer programs and better support for hardware :)

---

### Post by petit.padavoine on 2007-02-17
I don't know about the install but you could see if Linux really doesn't recognize your HD with a Live CD.
Boot up the system from the Live CD, open a terminal, and run the command
```
ls /dev/hd*
```
This will list all the hard disk devices Linux recognizes.
Each /dev/hd[letter] is a drive, each /dev/hd[letter][number] is a partition.
/dev/hdd is the CD-ROM drive.
If you can't see your drive, I guess Linux doesn't support it... (yet). Or I'm missing some knowledge, which is very likely :D.

---

### Post by mcduck on 2007-02-17
> **petit.padavoine said:**
> I don't know about the install but you could see if Linux really doesn't recognize your HD with a Live CD.
Boot up the system from the Live CD, open a terminal, and run the command
```
ls /dev/hd*
```
This will list all the hard disk devices Linux recognizes.
Each /dev/hd[letter] is a drive, each /dev/hd[letter][number] is a partition.
/dev/hdd is the CD-ROM drive.
If you can't see your drive, I guess Linux doesn't support it... (yet). Or I'm missing some knowledge, which is very likely :D.
That's not going to work, as only PATA drives are named /dev/hdxx.. For SATA and removable drives it's /dev/sdxx..

'sudo fdisk -l' lists all disks & partitions :)

---

### Post by petit.padavoine on 2007-02-17
> **mcduck said:**
> That's not going to work, as only PATA drives are named /dev/hdxx.. For SATA and removable drives it's /dev/sdxx..

I just learned something ;), thanks.

---

### Post by mskobier on 2007-02-17
All,
    Thanks for the replies. I have made some headway, but still not enough. Here is where I presenatl am at with the system.

I installed an old 20gig ide drive and installed 6.06 on it. It installed fine except for a few minor driver issues. It even supported the on board video and lan. I haven't tried the audio and have been researching the wireless lan card. Found Linux drivers for all, just need to figure out how to install them. 

Now for the SATA issue. In device manager, the system sees the on board SATA chip, but does not recognize them as drives. I have tried it in both AHCI and IDE mode. Neither way works. There is a linux driver for the SATA that came on the manufactures disk. Again, I haven't figured out how to install the drivers. All I have been able to find is general instructions. I guess the people who wrote them think we all know how to program in linux. Anyway, I think things are progressing, just need to learn a bit more about compiling the kernel. Anyone know of a good beginners web page that can walk me through a driver install?? Her are the instructions for installing the SATA driver that came with the manufactures disk:

Please copy this file to /tmp
1.tar -zxvf via-sata.tgz 
2.make 
3.modprobe sata_via 

I understand what they want me to do, just do not know how to do it!

Spike-X
     I too had trouble installing Windows XP on the SATA drive in another system. The trick is to get the SATA driver installed early in the setup of XP. When starting a fresh install, you will get a message on the bottom of the first screen asking you " to install third party scsi or RAID drivers, press F6" you need to be pretty quick( you have about 10sec to press F6). You will be asked for the driver to be on a floppy disk a few screens later. That should resolve your install problems with the SATA and XP. I have a couple of systems running with SATA and that has worked every time. Make sure in BIOS that the on board SATA is enabled or if you are using a seperate card, it needs to be disabled. You will still have to do the F6 thing either way. I have found it also helps if you have already Partioned the SATA drive. Fdisk has no problem seeing it on most any system. I just let it use the max available drive space on initial setup. XP will reconfigure it anyway.

Mitch

I hope that helped

---

### Post by NeoGreen on 2007-02-17
I am having that exact problem right now trying to install Ubuntu 6.10 on a SATA HDD.  I looked in the Bios and didn't see an option for a SATA driver.  But that seem really strange because I have connections for a SATA on my mobo.

---

### Post by mskobier on 2007-02-17
Nono,
       I guess it depends on which version of bios your MB has. I have two versions of the  A8V, one is the A8V Delux and the other is an A8V-VM. The Delux only has "On board SATA". enable, disable. It also has a Promise Raid chip with the same oprions. The A8V-VM has RAID, IDE, AHCI and disable. I would think it would be some variation of those. Either way, you still need the driver since the VIA, Promise or Adaptec( in another machine) all need the driver before XP or Linux will see them. What I plan on doing is as soon as I get the drive functioning, I am going to Migrate all the stuff form the old IDE to the new SATA. It appears that it should not be that difficult to do under Linux. 

Mitch

---

### Post by Spike-X on 2007-02-17
> **mskobier said:**
> 
Spike-X
     I too had trouble installing Windows XP on the SATA drive in another system. The trick is to get the SATA driver installed early in the setup of XP. When starting a fresh install, you will get a message on the bottom of the first screen asking you " to install third party scsi or RAID drivers, press F6" you need to be pretty quick( you have about 10sec to press F6). You will be asked for the driver to be on a floppy disk a few screens later. That should resolve your install problems with the SATA and XP. I have a couple of systems running with SATA and that has worked every time. Make sure in BIOS that the on board SATA is enabled or if you are using a seperate card, it needs to be disabled. You will still have to do the F6 thing either way. I have found it also helps if you have already Partioned the SATA drive. Fdisk has no problem seeing it on most any system. I just let it use the max available drive space on initial setup. XP will reconfigure it anyway.

Mitch

I hope that helped

Gigabyte motherboards in general have trouble recognising SATA drives when installing Windows, I found out later. I tried the trick with the RAID drivers on floppy, but either I had the wrong drivers or it just plain didn't work. 

I was able to work around the problem by pulling the IDE HD out of my old computer and using that as boot drive. I've since cloned that install onto a fresh IDE drive (the old one was making some nasty sounds) and that's what I'm using as my dual-boot drive now.

Thanks for the tip about partitioning the drive first. However, that wouldn't have worked, as it was a fresh system I was building, so I had no way of partitioning the drive until installation. It did seem to install Windows onto the drive the first time, but I then couldn't boot from it.

Thanks for the tips, though! I may be able to use them again some time.

---

### Post by NeoGreen on 2007-02-17
Yeah, I have a Shuttle XPC that I built myself from a Barebone kit. I looked under the manufacturers website and didn't see any updates for the Bios.

---

### Post by mskobier on 2007-02-17
All,
    This is just a bump. Last one. Hopefully someone can help me sort this problem out. Thanks again all.

Mitch

---

### Post by nonewmsgs on 2007-02-17
heh.  i had a similar problem, but my sata drives are on a pci card.  it used to freeze at 15% installation until i just unplugged them both.  im thinking ill flash my bios and maybe magic will happen so i can have more disk space.  it is - after all - the final frontier.

---

### Post by lwc on 2007-02-18
> **mskobier said:**
> First the system. This is an AMD64 3000 with 1gig ram on a ASUS A8V-VM with integrated graphics, a 300gig Seagate SATA drive using the onboard VIA southbridge controller(VT8251).

You're lucky. I am using a uLi M1585 SATA (onboard in an Asus P5RD2-VM) w/ the same 300G Seagate SATA drive. The Edgy CD doesn't even boot.

---

### Post by mskobier on 2007-02-18
All,
     Much headway since I last posted. I did a bit more research and thinking and discovered a few things. First, I was not running the 64bit version of Ubuntu 6.10. I had installed the 6.06-386 version. secondly, I discovered there was not any direct support for SATA drives in 6.06 due to the kernel version. I can not remember which version it is implemented in, but the 6.10 is current enough. I did an install of 6.10-386, and lo and behold, it identified the VT8251, installed the approprite drivers and allowed me to install to the SATA drive!!! I was having a hang issue during install at 49%. I replaced the CD drive with the second DVD drive from my primary computer and tried again. this time it isntalled without any problems. I have currently dumped the 6.10-386 version and  installed the 6.10 amd64 version. Its installed fine. It also seemed to be install a bit faster than the previous versions. It takes about 15min for a complete install. Under 6.10-386, the graphcs in Firefox was incredibly clunky and slow. Also the initial graphic display appears to be black and white. It is this way in both the live CD and when booting from the HD. However it appears to work fine once the desktop is running. The video is still clunmy under 6.10-64. Under 6.06, the video worked just fine with no hint of problems.  At least the system is working. Now just to sort out the video drivers. I did find a web page that has a step by step turotial on how to update the video driver. I tried it under 6.10-386, but was unable to complete the update due to directory configuration issues. Hopefully this new version will not have that problem.  Anyway, at least the SATA drive is working and appears to be working properly. one problem solved, just a few more to go.

Mitch

---

### Post by kinematic on 2007-02-18
> **mskobier said:**
> secondly, I discovered there was not any direct support for SATA drives in 6.06 due to the kernel version.

yes there is.
i installed 6.06 on a sata drive.

---

### Post by mcduck on 2007-02-18
> **mskobier said:**
>  secondly, I discovered there was not any direct support for SATA drives in 6.06 due to the kernel version.


I've been running Ubuntu on a SATA drive since 5.04 (which was the first Ubuntu verion I installed, I suppose even older ones would support SATA). It has always worked out-of-the-box for me..

---

### Post by mskobier on 2007-02-18
Kinematic, McDuck,
       I have been trying for the better part of a week to get 6.06 to recognize the SATA drive connected to the Via VT 8251 SATA chip with no luck. I tried it behind an old IDE drive and still no luck. I have read everything I could find to try and figure out how to make it work. As you can see, I even posted on this forum looking for help in solving the problem. I guess I should have stated that there did not appear to be support fot the VT 8251. I stand corrected. I guess I should not make blanket statements until I have all the facts.

Has anyone or does anyone ko=now how to fix the problem with the VIA K8M890 chrome9 GPU?

Thanks
Mitch

---

### Post by Toontje on 2007-02-19
In my opinion the problem is your chipset which is not recognized by the kernel (yet). The IDE drive can work on a generic driver but cannot enable DMA.

Later kernels probably support your chipset, so also your SATA drive.

I also have a ASUS board with the VT8237A chip, where I cannot enable DMA on my PATA drives

---

### Post by mskobier on 2007-02-19
Toontje,
      Thanks for the response. This has been quite an adventure. Reminded me of my old CPM/msdos days. Long before the internet! Yes I am that old! I think I touched my first computer about 1979 and was on line at 150 baud! I haven't played with a command line in a very long time. It was actually quite fun once I learned a few necessary commands. 

You are correct about chip set support being the issue. I rebuilt the system with 6.10_64 for the AMD64 and it recognized the chips and allowed me to set up the SATA drive. 6.06 would not do that. As of now, I have the system fully functional with both wired and wireless lan capability( on board lan disabled in bios). The DVD has a minor  issue of occassional vertical lines showing up during playback, but working none the less. There are a few more things I want to do to the system, but those will come in time. 

As for the SATA issue, if you haven't already, I recommend upgrading to 6.10. That seemed to correct the majority of my problems. Now, 6.10 will still not recognize the onboard video chip, but it will install the VESA drivers which will get the system running(slowly) then you can install the correct drivers. I currently have the OpenChrome drivers for the VIA K8M890 installed. I do want to eventually change them to the VIA provided drivers. They are available, but the script that comes with them does not work with Ubuntu. They will have to be modified before they will work. They are a good starting point though.

Again, thanks to everyone for the help. Hopefully I can help someone in the future.

Mitch

---

