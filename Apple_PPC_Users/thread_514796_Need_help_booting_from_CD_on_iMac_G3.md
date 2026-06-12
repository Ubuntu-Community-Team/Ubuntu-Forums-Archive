---
title: "Need help booting from CD on iMac G3"
date: 2007-08-01
forum: Apple PPC Users
---

### Post by potherca on 2007-08-01
Hi All, 
I've been running Ubuntu for quite a while now and I really like it, so much so I've basically been installing it on any PC I could find (with users permission ofcourse :))  I've never had any problem before but now I'm trying something new, I'm trying to install Ubuntu on an iMac but I just can't get the damned thing to boot from the CD. Seeing as I am new to mac I was wondering if I could get some help here... (My experience at this point consists of ready nearly any forum post I could find on iMacs in an attempt to boot from CD)

The mac I want to intall on is a friends iMac with a 450MHz PowerPC G3 processor and 64 MB SDRAM (I intend on putting more RAM in as soon as I can find my box with computer lefovers, I just moved so my life is still in boxes at the moment...) running OS 9. He got the computer without any CDs/manuals/etc. 
The steps are:
1. download the right ISO
2. burn it to CD
3. Boot from CD and install

I think I got the right ISO thanks to this forum but I think I might not be burning it properly... All I got to burn it with is my laptop which runs Vista (It's the next candidate to install Ubuntu on) using Nero BurningROM 7. The CDs boot fine on windows machines but do nothing for the Mac. I'm thinking maybe the problem lies there. I tried all the usual Mac boot tricks lying about on forums... the 'c' button... fucntion+mac button+o+f and boot the cd from the openfirmware interface... using the 'boot from disk' tool in the OS (which tells me there is no operating system on the CD). All to no avail.

I read somewhere that it might be possible to download the whole deal to the HD and boot it from there using some OpenFirmware commands, so I'm thinking about trying that. 
Also I saw
[ >  It works, but there's a bug that causes 6.06 not to work on seemingly-random machines.]("http://ubuntuforums.org/showthread.php?t=236871")  
Maybe that's the problem?

ANY hints or help would be greatly apreciated at this point...
Thanks.

---

### Post by Midwest-Linux on 2007-08-01
> **potherca said:**
> Hi All, 
I've been running Ubuntu for quite a while now and I really like it, so much so I've basically been installing it on any PC I could find (with users permission ofcourse :))  I've never had any problem before but now I'm trying something new, I'm trying to install Ubuntu on an iMac but I just can't get the damned thing to boot from the CD. Seeing as I am new to mac I was wondering if I could get some help here... (My experience at this point consists of ready nearly any forum post I could find on iMacs in an attempt to boot from CD)

The mac I want to intall on is a friends iMac with a 450MHz PowerPC G3 processor and 64 MB SDRAM (I intend on putting more RAM in as soon as I can find my box with computer lefovers, I just moved so my life is still in boxes at the moment...) running OS 9. He got the computer without any CDs/manuals/etc. 
The steps are:
1. download the right ISO
2. burn it to CD
3. Boot from CD and install

I think I got the right ISO thanks to this forum but I think I might not be burning it properly... All I got to burn it with is my laptop which runs Vista (It's the next candidate to install Ubuntu on) using Nero BurningROM 7. The CDs boot fine on windows machines but do nothing for the Mac. I'm thinking maybe the problem lies there. I tried all the usual Mac boot tricks lying about on forums... the 'c' button... fucntion+mac button+o+f and boot the cd from the openfirmware interface... using the 'boot from disk' tool in the OS (which tells me there is no operating system on the CD). All to no avail.

I read somewhere that it might be possible to download the whole deal to the HD and boot it from there using some OpenFirmware commands, so I'm thinking about trying that. 
Also I saw
  
Maybe that's the problem?

ANY hints or help would be greatly apreciated at this point...
Thanks.



64 MB Ram will not cut it with the live CD (Requires 256 or better) and I think the text based installer ALTERNATE CD will require at least 128 MB Ram, double check to make sure it is the PPC version.

---

### Post by potherca on 2007-08-01
The official thingy says 
> To run the Desktop CD (LiveCD + Install CD), you need 128 MB RAM to run or 192 MB RAM to install. The Alternate Install CD only required you to have 64 MB RAM.

The ISO I have is **xubuntu-6.06.1-desktop-powerpc.iso** since I plan on upgrading the PC to more RAM I thought I'd try to see if I can get the CD to boot first. If not having enough RAM causes the CD to not boot I shall have to get the alternate ISO instead, **xubuntu-6.06.1-alternate-powerpc.iso**.

---

