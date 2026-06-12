---
title: "Anyone sucessfully installed Ubuntu on ASUS Rampage IV Extreme"
date: 2012-09-26
forum: Asus Ubuntu Support (CLOSED)
---

### Post by grobaldo on 2012-09-26
Good morning all,
 
I've been trying without any luck to install Ubuntu on my rig . I am new to linux and can use help. Does Ubuntu support the main board? If so, what am I doing wrong? 
 
The main board is the ASUS Rampage IV Extreme. The CPU is a second generation i7-3960x with 16.0GB RAM. The Video Garphics Adapter is the EVGA GTX580. The CPU is liquid cooled.  And yes I over clock.
 
Am I doomed to have to run Windows 7 on this thing?
 
Regards,

---

### Post by amerinde on 2012-10-07
actually, yes, it works. thats what i am running. install wont work on the raid. I tried that at first. doesnt seem to have the drives.

---

### Post by Aerospaztic on 2012-10-16
So what does that mean?  I'm trying to install 12.04 after having Windows 7 (I want the whole drive for Linux instead), but I get a black screen with a single line cursor.  The black screen happens after I leave the installer main menu screen (Install from Disc, Try Ubuntu First before Installing, MEM test, and whatever else).

---

### Post by xgamer75 on 2013-01-24
Hi, I have the same problem that [Aerospaztic]("http://ubuntuforums.org/member.php?u=687967"), what we need to do to install ubuntu in this motherboard.

Regards

---

### Post by geogur on 2013-01-25
i`m having the same problem i cant get rid of windows , i want to install ubuntu 12.10  i even bought a usb from ubuntu.com but will not install

---

### Post by geogur on 2013-01-25
for some reason asus has embeded windows 7 on  my laptop so good i cant uninstall widows it will not work . what can i do to get around this all i want is ubuntu

---

### Post by oldfred on 2013-01-25
Do you also have the nVidia video card as that was his issue with black screen. nomodeset is required to boot liveCD/DVD/Flash drive.

If Windows 7 is pre-installed is it in BIOS/MBR mode or UEFI/gpt. Most Intel i-series based motherboards have both UEFI & BIOS modes.
If BIOS mode you may have 4 primary partition limit. If UEFI you need to boot in UEFI mode from live installer.

While same motherboard boot issues are almost always different as users have different configurations. Best to start your own thread.

---

### Post by xgamer75 on 2013-01-27
I´m new with ubuntu, what is nomodeset?, I have SLI asus GTX560 448 core and 2 plextor MD5 256 Gb in raid 0. And I try to install in only 1 hd 500 gb and i have black screen after 5 min the cpu hang...

---

### Post by oldfred on 2013-01-27
How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

With nVidia you need nomodeset on liveCD/DVD/flash and then on first boot. Once you install the proprietary nVidia from Ubuntu's repository it should just work. If 12.10 you need to install kernel headers first.

[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)

Why RAID 0? Especially with SSDs. Backups then are very important.

 Do not use gparted on RAID.
[http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)
Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
parted (3.0) completely removes filesystem creation and modification support, except for filesystem probing to determine what's in a partition.

---

### Post by ImperfectLink on 2013-05-27
I have Ubuntu 13.04 dual booting with Win7 on my R4E. Mine is also overclocked and didn't present a hurdle. Since I installed Win7 on EFI, I found that I also had to boot the install disc in UEFI mode. After that you just install as usual. The install was on two separate HDD's though.

Once you have Ubuntu 13.04 installed on one and Win7 on the other, you just set one of them as the default boot option in the firmware and if you want the other, just tap F8 during boot and it will give you the option. I found it more convenient than adding another layer to the boot process.

---

### Post by jfrez on 2013-06-12
I did it. I tried:

[LIST=1]
[*]NOMODESET : NOT WORKING
[*]12.10 x64 and x32 : NOT WORKING
[*]13.04 or 13.10 x64 and x32 : NOT WORKING
[*]10.10 x32 : WORKING!!!!! O_O
[/LIST]

Yes i know... 10.10 it not supported, is not a lts, and its not  x64 , but it works. I dont know why.....

---

### Post by billy-d on 2014-01-21
I know this thread is 6 months since last post but I found it with google and thought I'd throw in an update for anyone looking this up.

I am currently running 13.04 on Rampage IV Extreme

You should update to the latest bios and either turn off secure boot in bios or change the default setting from "Windows" to "Other OS".

If you have secure boot on, you need to install Ubuntu to a different hard drive than the main OS drive.

If you turn secure boot off, you can install alongside Windows up to Windows 7. Windows 8 freaks out.

Currently I'm running multiple hard drives, one has Windows 8 and the other Ubuntu 13.04, I have no problems.

However if you do this, to get dual boot to work right you must:

Make sure the boot loader is installed on the Ubuntu drive.
Point the first boot device as the Ubuntu drive.

Ubuntu will see Windows and give you the dual boot option.
However Windows 8 will NOT boot Ubuntu (very selfish).

Also, if you want to be able to access the Windows 8 drive from Ubuntu, you have to turn fastboot off inside Windows 8 and make sure your power buttons don't hibernate, but fully shut down.

If it helps, I did not use live CD, booted installer directly.

---

