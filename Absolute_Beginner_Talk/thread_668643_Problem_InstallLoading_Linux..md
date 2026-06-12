---
title: "Problem Install/Loading Linux."
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by kost on 2008-01-15
Hello and Congratulations on your good work. I am newbie here, and here is my story:

- I downloaded from official site Ubuntu.com Desktop Edition 7.10 for 64bit Intel and AMD Processors.

- I burntthe iso I downloadedwith Nero 8 twice (with speed x42 (max) and a x24 (in order to I see if there was a problem with the burn; but there was not)

- The problem I experience goes like that: I have installed Windows XP SP2 x86 (32bit) in my hard disk. What I want to make is to dual boot with Linux Ubuntu 7.10. I insert my CD and I make restart of PC in order that I proceed to boot from CD so I can start to install. I select the first option (Start or Install Ubuntu) and begin in a classic windows saying: “Loading Linux Kernel” with some number on %. After it loads completely, it shows as if it was running certain lines in terminal (very likely, first time I put Linux) or something as M$DOS (command prompt). Later from that, blackens the screen and it says “Going to sleep” happens when no signal is transmitted to from my PC to my Monitor. I after chose the option that says ("Test CD For defects", and again it starts loading kernel and then poof, "Going to sleep". Please help me. I want to install Ubuntu desperately..


Thank's in advance

kost

P.S My PC Specs

```
Processor Information:
    Vendor:  GenuineIntel
    Speed: 1334 Mhz
    4 logical processors
    4 physical processors

Windows Version:
    Windows XP (32 bit)
    NTFS:  Supported

Video Card:
    Driver:  NVIDIA GeForce 8800 GTX
    DirectX Driver Name:  nv4_disp.dll
    Driver Version:  6.14.10.9744
    DirectX Driver Version:  6.14.10.9744
    Driver Date: 5 Dec 2006
    Desktop Color Depth: 32 bits per pixel
    Monitor Refresh Rate: 75 Hz
    DirectX Card: NVIDIA GeForce 8800 GTX
    VendorID:  0x10de
    DeviceID:  0x191
    Number of Monitors:  1
    Number of Video Cards:  1
    No SLI or Crossfire Detected
    Primary Display Resolution:  1024 x 768
    Desktop Resolution: 1024 x 768
    Primary Display Size: 11.81" x 8.86"  (14.76" diag)
                                            30.0cm x 22.5cm  (37.5cm diag)
    Primary Display Type: CRT
    Primary Bus: PCI Express 16x
    Primary AGP GART Not Detected
    Primary VRAM: 768 MB
    Primary Monitor Vendor:  Compaq
    Primary Monitor Model:  Compaq 1501
    Supported MSAA Modes:  2x 4x 8x 


Memory:
    RAM:  2046 Mb
```

---

### Post by buntunub on 2008-01-15
Impossible to know what the issue is without knowing what messages that it spits out when things go wrong. In any case, you  most likely have a bad burn. Try burning the ISO at speed x4.

---

### Post by kost on 2008-01-15
I made it work. I deleted quite splash and added avg=ask in the boot line.. But now I cant install them. I mean I go throu 1 and 2 steps and then in the partition manager as I select to resize the partition, I confirm and then it says Error: Failed to resize partition aborting.. And now I can only choose only the other 3 options left (Guided Entire Disk Manual etc)
Any ideas??

Thanks,

kost

---

### Post by Sef on 2008-01-15
1) Did you reburn the iso at 4x or slower? (Faster can corrupt the download.)

2) Did you [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") the download?

3) Read [Psychocat's installing]("http://www.psychocats.net/ubuntu/installing").

---

### Post by Sinkingships7 on 2008-01-15
you're trying to install a 64bit version of ubuntu on a 32bit based PC, from what i can see.
tell me if i'm wrong.

if i'm right, then that is simply against the rules and you'll have to download and burn the 32bit version.

---

### Post by kost on 2008-01-16
Well, I have used 32bit version for windows xp.. But now I use ubuntu 64bit.. I just want to partition them. Isnt it possible to have 1 32bit on A partition and 1 64bit on another?

kost

---

### Post by PeterJS on 2008-01-16
It's not a matter of partitions. The problem is you have a 32bit CPU (well 4 of 'em), and no amount of cleverness in the world is going to get 64 bit software to run on 32 bit hardware.

---

### Post by kost on 2008-01-16
> **PeterJS said:**
> It's not a matter of partitions. The problem is you have a 32bit CPU (well 4 of 'em), and no amount of cleverness in the world is going to get 64 bit software to run on 32 bit hardware.
Well, I am more than sure that my PC supports 64bit OSes because I used to use Windows Vista Ultimate x64.. Plus, I have a program Installed (Tune Up Utilities 2008) Which actually tells me that I should upgrade to 64bit OS because my hardware supports it and it will go faster etc..

kost

---

### Post by dstew on 2008-01-16
Choose Manual to partition. Take a screenshot of the partition manager screen and post it to the forum if it is not working. Use alt-PrtSc key combination to take a picture of the active window.

---

### Post by kost on 2008-01-16
I used alt-prsc and what should I do now?? T_T

EDIT: NVM I fixed it:

---

### Post by dstew on 2008-01-16
I assume you want to create a new partition for Ubuntu on your /dev/sda1 disk, which at present is wholly occupied by the Windows NTFS file system, correct? To do this, you need to shrink the NTFS partition, and create a new ext3-formatted partition from the unallocated space. Have you defragmented the NTFS yet?

---

### Post by kost on 2008-01-16
Ehmm, I think I did somedays ago with TuneUp Utilities in windows.. But how to do it anyway.. Yes correct.. I want to add ubuntu to the thing with 320GB ;)

---

### Post by kost on 2008-01-16
***Bumpin*** < Sry for that :x

---

### Post by dstew on 2008-01-16
Use the defragmentation tool in your Windows system. My Computer --> right click the drive --> Properties --> Tools tab --> Defragment Now

---

### Post by kost on 2008-01-16
Ok and after that?

---

### Post by dstew on 2008-01-16
Go back to installing Ubuntu, and shrink the NTFS partition from the right.

---

### Post by buntunub on 2008-01-16
> **kost said:**
> Well, I have used 32bit version for windows xp.. But now I use ubuntu 64bit.. I just want to partition them. Isnt it possible to have 1 32bit on A partition and 1 64bit on another?

kost

:popcorn:

If your system supports a 64 bit OS, then yes, that would work.

---

### Post by kost on 2008-01-16
> **dstew said:**
> Go back to installing Ubuntu, and shrink the NTFS partition from the right.
How to do that?? O_o

---

### Post by dstew on 2008-01-16
When you get to the partitioning screen, use Guided and move the slider from the left to the right to choose a new size. Whatever is left over will be unallocated space.

---

### Post by kost on 2008-01-16
> **dstew said:**
> When you get to the partitioning screen, use Guided and move the slider from the left to the right to choose a new size. Whatever is left over will be unallocated space.
Ok mate, thanks and sorry for n00bing all the time T_T.. 
Wait, I will come back with my result.. Peace, kost

---

