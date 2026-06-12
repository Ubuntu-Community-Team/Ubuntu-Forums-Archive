---
title: "Dual boot/ GRUB loader question"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by thinktyler on 2007-07-23
I dual booted Ubuntu with XP SP2, the guide I used apcmag.com/dualboot worked perfect for me. I believe I got some misleading advice, as I was told that when I wanted to delete windows sp2, I could just delete the partition. So I fired up GNOME partitioner and deleted the partition. 

When  I try booting to XP on the grub loader, so I can insert a new live cd nothing boots. In fact, Ubuntu 7.04 live cd doesn't boot nor does GNOME Partitioner. 

I checked the boot order, but my cd-rom appears to be listed as USB CD-ROM. I find it hard to believe my bios doesn't detect my CD-ROM because I have dual booted multiple times different OS. 

I want to dual boot Vista and Linux now. But I can't use any livecd's or boot Vista setup to overwrite the MBR. Now the information I have pulled on what I should do is unclear. Any tips or suggestions or tutorials would help me out. 

Linuxquestions.org had an interesting forum on re-installing the grub, but I don't think that will help me in my case. 

Thanks.

---

### Post by ReaderRat on 2007-07-23
Use a partitioner and delete ALL partitions and start from scratch - re-install everything to a fresh, clean hard disk.

[[color=blue]Dual-Boot (1 HDD)[/color]](http://apcmag.com/node/5162/)

---

### Post by thinktyler on 2007-07-23
GNOME paritioner doesn't boot and I can't unmount it while in Ubuntu. How do I unlock the partition so I can delete it and create a new partition?

---

### Post by ReaderRat on 2007-07-23
I believe you need to get the problem with your BIOS & CD-ROM fixed before you go any further with the partitioner.
 I don't know what's wrong, so I will **Bump** you where someone else can help you.

---

### Post by thinktyler on 2007-07-23
Thank you,  I have a MIT670SHISHUMA 845j DVD-RW/DL in an acer 5670 and I cannot boot to CD-ROM because in the boot loader it only has USB CD-ROM as an option.

---

### Post by thinktyler on 2007-07-24
I did see something fairly unusual. The USB CD-ROM listed says "USB CD-ROM APPLE iPOD" ... Could it be that my CD-ROM is not being detected, but my iPOD is somehow screwing with the boot?

I unplugged my ipod and I still get same results.

---

### Post by Orochi on 2007-07-24
I'm not sure I completely understand what's happening. You're saying you had a dual boot with XP and Ubuntu, and then you deleted the XP partition. But then you say you try to boot into XP, which is obviosuly impossible since you just deleted it. Are you trying to reinstall XP? What are you trying to do or install, and what is the current setup on your harddrive?

---

### Post by thinktyler on 2007-07-24
I dual booted Ubuntu + XP. However, I don't want XP anymore. So I deleted the partition. Now it seems I'm unable to boot from any disc and when I do select "XP" from the grub loader I get "kernel is missing insert setup disk and reboot" error. My friend gave me Vista for free, so I wanted to try it and install it over the XP partition. I hope that makes it clear.

Basically, I want Ubuntu + Vista dual booted. Vista setup on the partition b.

---

### Post by thinktyler on 2007-07-25
Would buying a new CD-ROM or USB CD-ROM fix me not being able to boot the VISTA/Ubuntu installs?

---

### Post by Raineer on 2007-07-25
I wouldn't buy a new one yet, maybe try defaulting your BIOS...either by selecting a default option in the menu or moving the BIOS default jumper on your motherboard (probably need to look online for this if you dont have the original docs).  It's the same as pulling the battery so the BIOS defaults itself.

There is no reason you can't boot to a CD, no operating system could mess that up.  I would boot with the "Gparted Live CD", just google that and boot it to do any partition work. It's wonderful.

---

### Post by Orochi on 2007-07-25
> **thinktyler said:**
> I dual booted Ubuntu + XP. However, I don't want XP anymore. So I deleted the partition. Now it seems I'm unable to boot from any disc and when I do select "XP" from the grub loader I get "kernel is missing insert setup disk and reboot" error. My friend gave me Vista for free, so I wanted to try it and install it over the XP partition. I hope that makes it clear.

Basically, I want Ubuntu + Vista dual booted. Vista setup on the partition b.

Can you still boot into Ubuntu from GRUB?

Like Raineer said, deleting partitions could not do anything that would make you unable to boot from CD. Some BIOS require you to press a button on startup to boot from the CD drive instead of the hard drive. Also check your BIOS settings to make sure CD is set to boot before your Hard drive. You should just be able to put the Vista CD in the drive and install it to the partition XP was on.

---

### Post by thinktyler on 2007-07-25
Thanks for the reply,

Yes I can boot into Ubuntu with no problems. I reset my BIOS settings to default. When I do this the HD appears to be above the "USB CD-ROM" so I moved the CD-ROM to the top. Still no change. Doing the hardware reset I will look into with more details. I have the gpart Live CD burned, but won't boot. But it is good news that the boot should work. I will be working on it all day.

I'm going to re-burn Gpartioner. 

When I select the grub launcher XP, I get a "kernel missing insert setup disk and reboot" .... What is giving me this message? Bios, GRUB, XP? 

Next step,
Checking BIOS Settings.

---

### Post by Orochi on 2007-07-25
You get errors when you select XP from GRUB because you deleted the XP partition, so there's nothing there to boot into.

It sounds like something got messed up in your BIOS that's making it boot from the harddrive instead of the CD. try reordering the boot order in the BIOS all different ways, or like I said check to see if your BIOS has a button that needs to be pressed/help down to boot from CD.

---

### Post by thinktyler on 2007-07-25
Ok, I'm going to try every boot sequence. But, don't you think the fact that my CD-ROM is not USB, that I'm having troubles booting. I don't think I mentioned that earlier. Or it was very clear.

I don't have a USB CD-ROM.  It comes up as "USB CD-ROM Apple Ipod" ... which makes no sense.

I also want to note that I hear the CD/DVD being read by the CD-ROM. It makes the same "sound" as if I was putting it in with Ubuntu loaded. It seems like something is trying to load, but for whatever reason it cannot.

Ok, thanks for the help. I'm sure I will get this problem fixed shortly.

---

### Post by thinktyler on 2007-07-25
I looked throught countless articles, I'm not exactly sure wether what I did caused my CD-ROM to longer boot, so I can't narrow the problem. 

But, in order for it to get it working i'm going to do a few things.

I'm going to buy a external DVD drive which hopefully will boot, then upgrade my BIOS through VISTA. As my technical knowledge is limited on the linux side, (hopefully i'll be more l33t with college, lol) ... 

I will start this process tomorrow if you have any advice or tips... if im going to screw something up please let me know. 

Thanks for the helping hands so far.

---

