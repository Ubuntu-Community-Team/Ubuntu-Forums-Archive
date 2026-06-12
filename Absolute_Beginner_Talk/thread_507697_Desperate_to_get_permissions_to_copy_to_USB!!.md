---
title: "Desperate to get permissions to copy to USB!!"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by intransit on 2007-07-23
Hey all

Just finally managed to get X thing to stop crashing on me and have got ubuntu 7.04 going on my laptop. I've got it running on a live cd in an attempt to save my files cos the hard drive seems to have gotten corrupted. anyway i'm trying to copy files from the hard drive to my usb thumb drive 512 mb, the first time i tried it worked and i got a folder across, then next time it tells me that i dont have the rights to.

have searched the forums btu they all seem to be talking about external hard drives and doesn't seem to answer my question. sorry for the newbie question, but please help!

---

### Post by kirios on 2007-07-23
[COLOR="DarkRed"]Type **mount** in a terminal. This will tell you where your USB disk (/dev/sda or something similar) is mounted on the filesystem (e.g., /media/disk). Then type **sudo chmod o+w /media/disk** (if that's where your disk is mounted).[/COLOR]

---

### Post by asmoore82 on 2007-07-23
I've seen something like this before...

try creating a folder on the USB drive and copying all the files into that new folder

---

### Post by intransit on 2007-07-23
thanks guys

@ asmoore, that was i originally tried. I got one folder over then it all tripped out and i think it might have bugged out my usb drive a bit (as in corrupted file) but don't know went to back it up and it on another comp and it was telling me some files were corrupted and couldn't be copied. not ones copied from the bad hd ones i'd had on there earlier, i'd understand if ones id copied from the hd were bad, but nevertheless, they may have become corrupt some way anyway)

@kirios, i get

/dev/hda1 on /media/disk type ntfs (rw,nosuid,nodev,umask=222,utf8)
/dev/sda1 on /media/KINGSTON type vfat (rw, nosuid, nodev, shortname=mixed,uid=999,....utf8,

the kingston is the name of the usb so i assume i do the command on the kingston one i.e

sudo chmod o+w /media/KINGSTON

---

### Post by intransit on 2007-07-23
thanks guys

@ asmoore, that was i originally tried. I got one folder over then it all tripped out and i think it might have bugged out my usb drive a bit (as in corrupted file) but don't know went to back it up and it on another comp and it was telling me some files were corrupted and couldn't be copied. not ones copied from the bad hd ones i'd had on there earlier, i'd understand if ones id copied from the hd were bad, but nevertheless, they may have become corrupt some way anyway)

@kirios, i get

/dev/hda1 on /media/disk type ntfs (rw,nosuid,nodev,umask=222,utf8)
/dev/sda1 on /media/KINGSTON type vfat (rw, nosuid, nodev, shortname=mixed,uid=999,....utf8,

the kingston is the name of the usb so i assume i do the command on the kingston one i.e

sudo chmod o+w /media/KINGSTON

---

### Post by intransit on 2007-07-23
sorry for the double post

that seemed to work, and let me copy files over

but now neither computers can recognize the usb. i wonder if it just died or it was something i did to it?

perhaps theres a better method, we have a windows xp network here with internet sharing, if i plugged in the network cable would the internet work? and then i could send the files across one of those websites

---

### Post by kirios on 2007-07-23
Yes, you could transfer the files over the network (after entering TCP/IP settings). Could you post the output of **dmesg | tail** (curious about your USB drive).

---

### Post by intransit on 2007-07-24
hi, sure:

```
ubuntu@ubuntu:~$ dmesg | tail
[54024.624000] sd 5:0:0:0: SCSI error: return code = 0x08000002
[54024.624000] sda: Current: sense key: Medium Error
[54024.624000]     Additional sense: No additional sense information
[54024.624000] Info fld=0x0
[54024.624000] end_request: I/O error, dev sda, sector 0
[54024.796000] sd 5:0:0:0: SCSI error: return code = 0x08000002
[54024.796000] sda: Current: sense key: Medium Error
[54024.796000]     Additional sense: No additional sense information
[54024.796000] Info fld=0x0
[54024.796000] end_request: I/O error, dev sda, sector 0
ubuntu@ubuntu:~$ 

```

I didn't check the status before I did the command, I just did it without waiting. Now both computers (windows and ubuntu) don't seem to recognize it. Strange. Maybe did I change the file format or something.

Anyway I've just got this connected to the network and internet sharing is working so i'm on the internet. So I guess i'll try emailing my file's or storing them online somewhere. Is it hard to set up file sharing with an xp network???

Thanks for all your help, greatly appreciated. Absolutely loving ubuntu, it's going to be the first thing I install once I recover my data and reformat. :) Cheers

---

### Post by intransit on 2007-07-24
Umm so it seems to recognize it again now, gets the name and everything, but won't let me browse it, and says unable to mount media (something about nothing on it)

Strange any ideas?

---

### Post by intransit on 2007-07-24
oh and with the usb out this is what i get

```
ubuntu@ubuntu:~$ dmesg | tail
[56190.780000] eth0: no IPv6 routers present
[56304.804000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[56328.712000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[56353.216000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[56377.520000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[56502.072000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[56625.376000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[56749.328000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[56824.564000] usb 3-1: USB disconnect, address 7
[56872.624000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
ubuntu@ubuntu:~$ 
```

---

### Post by kirios on 2007-07-24
> Now both computers (windows and ubuntu) don't seem to recognize it. Strange. Maybe did I change the file format or something.... Is it hard to set up file sharing with an xp network???
[COLOR="DarkRed"]I don't understand why  your USB disk isn't recognized but you could reformat it on a Windows PC and try again. 
Sharing files over a network is quite easy. Hope this link will help:[/COLOR]

[COLOR="Sienna"][https://help.ubuntu.com/7.04/server/C/windows-networking.html]("https://help.ubuntu.com/7.04/server/C/windows-networking.html")[/COLOR]

---

### Post by kevdog on 2007-07-24
Not sure if the error messages you last posted have anything to do with your problem, but bcm43xx is indicating a wireless device.  Are you sure your USB stick is a flash driver and not a USB wireless dongle -- I had one person confuse the two more than once!!

---

### Post by intransit on 2007-07-24
definetly not wireless, its a usb

my laptop has that inbuilt, and i assume i haven't disabled it as that message would pop up every 40 or so seconds in the console when i was trying to get X server to work and get into the desktop/ubuntu OS

I assumed it popped up as it would attempt to find a signal every 40 or so seconds and fail cos nothing is configured. Setting up Wifi is the next task, do you know if I can connect to VPN's with wifi?

Thanks I will look into sharing files as soon as I get home from uni.

How do i format my usb in windows? (sorry for the rediculously newbie question)

---

### Post by kirios on 2007-07-24
> How do i format my usb in windows? (sorry for the rediculously newbie question) 
[COLOR="Sienna"]Click on Start > All Programs > Administrative Tools > Computer Management. Right-click on your drive in the Computer Management window and select Format > FAT32.[/COLOR]

---

### Post by intransit on 2007-07-24
Thanks so much for bearing with me kirios,

Filesharing was much easier than I expected. Got it running no worries. Have already managed to save most my data, just copying the rest as we speak. Ubuntu rocks and microsoft sucks for dieing so hard. If it weren't for linux live cd's i wouldn't have been able to recover anything.

Just 2 final questions, to get me up and running again

1) So once i'm done copying all my data to my desktop windows comp, I want to reformat the corrupt laptop hd and get it going again. I want to get a dual boot going with xp and ubuntu. If everything is still working the way I left it if I don't put the live cd in to boot with, windows will give me the 4 boot options to choose from, safe mode, safe mode w/ networking,..., last good config, etc... if i chose a safe mode it hangs while loading driver/mup.sys or something, and last good config or normal will give a blue screen real quick then reboot.

So what are the steps I should take to properly reformating my drive and trying to get the drive healthy again with no corruptness like before, just reformat it? and how like - in ubuntu / live cd / windows recovery console ??

And then, to begin installing both OSes for dual boot, which one should I install first? I was reading some howto that said it'd be better with ubuntu first.

Thanks so much for all your patience and help in saving my important files!

---

### Post by intransit on 2007-07-24
oh sorry, the other quick question I had was,

the files I copy over from the laptop hd from ubuntu, are read only, does this matter?

I tried on one right click > remove tick from 'read only', and it worked without error message, so I guess it won't matter then? 
:)

---

### Post by kirios on 2007-07-24
> So what are the steps I should take to properly reformating my drive and trying to get the drive healthy again with no corruptness like before, just reformat it? and how like - in ubuntu / live cd / windows recovery console ??
And then, to begin installing both OSes for dual boot, which one should I install first? I was reading some howto that said it'd be better with ubuntu first.
[COLOR="DarkRed"]Since last good config and safe mode both fail to boot, you might as well reformat the hard drive while you're still running the Ubuntu live CD.  If you have a swap partition, run **sudo swapoff -a** first, then use Partition Editor in the System menu to delete all existing partitions. Make a primary FAT32 partition for Windows (/dev/hda1) - at least 20 GB if you plan to install more than a handful of Windows apps. Leave the rest of the disk as unallocated space for the time being.

It's easier if you install Windows first. Once Windows is up and running, boot from the Ubuntu CD again and start the Ubuntu installer. When you get to the partitioning step, choose Custom Partitioning and make a Linux partition (ext3) and a swap partition in the unallocated space. When the install completes, you'll be able to boot into the GRUB menu and choose either Ubuntu or Windows. :-)[/COLOR] 

> the files I copy over from the laptop hd from ubuntu, are read only, does this matter?
I tried on one right click > remove tick from 'read only', and it worked without error message
[COLOR="DarkRed"]It doesn't matter on Windows. You may need to change file permissions if the files are read-only in Ubuntu.[/COLOR]

---

### Post by intransit on 2007-07-24
I don't know if i have a swap partition, how do i check?

And I couldn't find a Partition Editor in the system menu. Maybe I need to apt-get it?

Just a question, by deleting the partitions, is that effectively reformatting the entire hard drive. E.g. if went straight to installing windows and gave it smaller partition then the whole HD, would the rest of it still contain junk or it would automatically reformat that to empty and just leave the partition i'm making.

Basically i'm wondering if it would just be easier if now I just followed this guide [http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty) Part 1

or I should first do the partition in ubuntu like you said. Because it seems that guide effectively achieves the same by specifying while installing windows a smaller partition for it leaving the rest unallocated. I'm a bit confused, hope you understand what i'm saying.

And thanks so much for all your help



edit: Just rebooted and now when I try to get into ubuntu (either start or install ubuntu or start ubuntu in safe graphics mode) it sits loading for ages and nothing happens when before it went almost straight into first screen....weird!? I changed settings in files while I was on the live cd but didn't think these would save to the cd, maybe if they did i corrupted something, which is weird anyway cos i only changed xorg.conf to get x server thing working and smb.conf to get networking working.. really strange...might ahve to install windows first now. or i could reburn the ubuntu iso incase the cd was changed but i really doubt that that would be weird but then again. Any ideas?

---

### Post by kirios on 2007-07-24
>  I don't know if i have a swap partition, how do i check?
And I couldn't find a Partition Editor in the system menu. 
Sorry, I forgot that Feisty doesn't include gparted by default. If you're still running the live CD, use parted from the command-line instead. 
```
sudo parted /dev/hda
```
If that doesn't work, try **sudo parted /dev/sda**. Type **p** to list all partitions on the hard drive (which will also identify swap partitions). To delete partitions, just enter **rm** and the number of each partition (one at a time, starting with the last partition): **rm 6** then **rm 5** and so on. Type **q** to exit. 

[COLOR="DarkRed"]Alternatively, you could boot from the Windows CD and delete all partitions in the setup screen, then follow the tutorial at [/COLOR][http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty]("http://http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty")

> Because it seems that guide effectively achieves the same by specifying while installing windows a smaller partition for it leaving the rest unallocated.
Yes.

> would the rest of it still contain junk or it would automatically reformat that to empty and just leave the partition i'm making.
Once you delete partitions, your hard disk becomes unallocated space until you format it with a file system. The 'junk' is technically still on the drive but you can't access it. 

> I changed settings in files while I was on the live cd but didn't think these would save to the cd
No, it shouldn't save settings to the CD. I think you should reformat the drive, get Windows up and running, then try again.

---

### Post by intransit on 2007-07-25
Ok cool, formatting a partition now looks like it's going to take sometime.

A question in the mean time, when i'm in windows, will I be able to see the ubuntu file system / partition ?
And when i'm in ubuntu will I be able to see the windows file system / partition ?

E.g. i'm just thinking of a central repository of mp3s, where it wouldn't matter which OS i log into, they will be able ot be accessed by both.

---

### Post by kirios on 2007-07-25
> when i'm in windows, will I be able to see the ubuntu file system / partition ?
[COLOR="DarkRed"]No, Windows can't access Linux file systems unless you use (experimental) drivers.[/COLOR]

> And when i'm in ubuntu will I be able to see the windows file system / partition ?
[COLOR="DarkRed"]Yes, it will be in /media by default.[/COLOR]

---

### Post by intransit on 2007-07-25
cool,

so i'll solve this just by having the shared mp3 area on the windows partition.

Thanks mate, you've solved all my problems for now!!

If only formatting didn't take so long! I'll be back when i'm onto the ubuntu install :)

---

### Post by intransit on 2007-07-25
****!

Setup on windows finished formatting the partition or whatever, took like 6 hours, took the long option rather than quick cos thought it would be better for my unhealthy disk to not take any shortcuts, anyway just after setup finished that and finished copying files (this screen: [http://images.howtoforge.com/images/dual_boot_windows_xp_ubuntu_feisty/xp5ns4.gif](http://images.howtoforge.com/images/dual_boot_windows_xp_ubuntu_feisty/xp5ns4.gif))

I get a nasty blue screen:

```

STOP: c0000221 Unknown Hard Error
\SystemRoot\System32\ntdll.dll

```

MS have a page, but its pretty useless in my situation [http://support.microsoft.com/default.aspx?scid=kb;en-us;Q314474](http://support.microsoft.com/default.aspx?scid=kb;en-us;Q314474)

God damn windows. Also found this thread [http://www.annoyances.org/exec/forum/winxp/t1030972927](http://www.annoyances.org/exec/forum/winxp/t1030972927)

I have this funny niggling idea that because the live cd isn't working anymore, maybe it could have something to do with my cd drive!? but it's been working fine till today. So weird.



Edit: So I got a different disk, was using xp home edition before now using xp proffesional, went thru deleted old partition of first butchered xp installation, and then remade the partition same size but this time in quick mode. Was much quicker, took like a minute and went to install, then I left computer came back, just black screen but power on, no cd lights hd access lights just on and could hear it on. So I restart without the boot cd, it goes into the windows loader with the blue cells moving side to side, then the screen just goes completely black. What on earth!?

As we speak i'm starting the 3rd or 4th reinstall of windows completely fresh. I wonder if the same thing will happen again? This is rediculous

---

