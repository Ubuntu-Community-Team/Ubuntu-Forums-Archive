---
title: "BSOD windows install"
date: 2011-12-07
forum: Any Other OS
---

### Post by The Kraken on 2011-12-07
A friend of mine gave me his old pc because it wouldnt boot into his  windows vista. i gave him an old copy of ubuntu 9.xx just so he could  get on the internet and trouble shoot his own problem. He ended up  getting a new tower. He recently passed it on to me thinking i would  have better luck. 

For some reason it will install and run the  latest version of ubuntu but it will not let me install windows at all. I  get a blue screen of death. 

My question is how do i get around the bsod to install windows? what should i be looking for that would cause this to happen?

Also,  i have another pc with windows on it. would it be possible to just  switch the hard drives? if so how much trouble could i expect to run  into?

Any help would be very much appreciated. If i need to give more info, just let me know.

Thanks.

---

### Post by newbie-user on 2011-12-07
BSOD is sometimes caused by hardware failure.  Also, I've seen BSOD when moving a hard drive from one computer to another and that's because Windows doesn't recognize the hardware anymore.

If you want to troubleshoot the hardware, I'd recommend starting with the ram.

---

### Post by bluexrider on 2011-12-07
> **The Kraken said:**
> A friend of mine gave me his old pc because it wouldnt boot into his  windows vista. i gave him an old copy of ubuntu 9.xx just so he could  get on the internet and trouble shoot his own problem. He ended up  getting a new tower. He recently passed it on to me thinking i would  have better luck. 

For some reason it will install and run the  latest version of ubuntu but it will not let me install windows at all. I  get a blue screen of death. 

My question is how do i get around the bsod to install windows? what should i be looking for that would cause this to happen?

Also,  i have another pc with windows on it. would it be possible to just  switch the hard drives? if so how much trouble could i expect to run  into?

Any help would be very much appreciated. If i need to give more info, just let me know.

Thanks.

BSOD could be hardware issues or problems with the HDD. May try to reformat the drive then do the install.

As far as switching the HDD's from one machine to the other is not advisable. the hardware signatures would likely not match resulting in an unusable machine

---

### Post by BC59 on 2011-12-07
What version of Windows you like to install?

What type of hard drive has your computer, is SATA or the older type IDE?

Exchanging the hard drives with Windows between computers is not recommended because normally your system is going to fail.

---

### Post by z2daj on 2011-12-07
Does it give you a BSoD directly out of a fresh install of Windows? Or are you completely un-able to install Windows... depending on the case, you could pinpoint where the error is occurring, whether in hardware or software.

---

### Post by bluexrider on 2011-12-07
> **z2daj said:**
> Does it give you a BSoD directly out of a fresh install of Windows? Or are you completely un-able to install Windows... depending on the case, you could pinpoint where the error is occurring, whether in hardware or software.


its Windows Viata.....is it worth saving?

---

### Post by lisati on 2011-12-07
Whether or not it's worth saving is a matter of opinion: I keep Windows around for some video editing software I use but would otherwise happily go 100% Ubuntu

I've seen BSOD arise from memory cards I installed myself bumping loose: reseating them in the sockets seemed to help.

---

### Post by bluexrider on 2011-12-07
> **lisati said:**
> Whether or not it's worth saving is a matter of opinion: I keep Windows around for some video editing software I use but would otherwise happily go 100% Ubuntu

I've seen BSOD arise from memory cards I installed myself bumping loose: reseating them in the sockets seemed to help.

I have a running W-XP on VM so as to use adobe lightroom and photoshop, but vista really

---

### Post by The Kraken on 2011-12-13
Thank you all for the quick responses. I was away for the weekend, but now im back.

So, Im trying to install WinXP, to clarify. Heres what happened since I've been back. I downloaded Ultimate Boot CD and ran some diagnostics. No problems with the ram, but none of the HDD utilities could find my hard drive. WTF! How is it possible that ubuntu can install and run on a hard drive that cant be found? 

I looked at the hard drive, unplugged it and plugged it back in. In the process i found that there were two cables to plug in. One was bigger than the other. Plugging the smaller one in didnt seem to matter. UBCD was still unable to find my hard drive.

The tower I have is a Gateway LX 6810-01. The hard drive itself is a 1.0 x 640.0 GB - Standard - Serial ATA-300 - 7200.0 rp.

Thanks again for the help.

---

### Post by BC59 on 2011-12-13
The one cable is for the data, the other for the power.

Can you boot from a Live CD? or bootable USB? then choose **Try Ubuntu**

---

### Post by The Kraken on 2011-12-13
I have ubuntu installed and running. Using it as my main comp at the moment. The problem is not being able to install windows. It goes through the set up process then give me a BSOD. I think I might just buy a new hard drive and try to install that. Still want to get this figured out though. 

It wouldnt have anything to do with drivers for the motherboard would it?

---

### Post by BC59 on 2011-12-13
Can you post the results of these commands?

```
sudo parted /dev/sda print 
sudo fdisk -l
```

---

### Post by The Kraken on 2011-12-13
sudo parted /dev/sda print:
```
Model: ATA WDC WD6400AAKS-2 (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  632GB  632GB   primary   ext4            boot
 2      632GB   640GB  8589MB  extended
 5      632GB   640GB  8589MB  logical   linux-swap(v1)
```
sudo fdisk -l
```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006053a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1233485823   616741888   83  Linux
/dev/sda2      1233487870  1250263039     8387585    5  Extended
/dev/sda5      1233487872  1250263039     8387584   82  Linux swap / Solaris

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1465144064   732572001    7  HPFS/NTFS/exFAT
```

---

### Post by BC59 on 2011-12-13
As you can see there is no Windows installed. There is only the Windows boot sector giving you the BSOD.

---

### Post by The Kraken on 2011-12-13
How do i get rid of that boot secotor, if i can? And if I get rid of it, will that allow me to install XP?

---

### Post by BC59 on 2011-12-13
There is no problem with it. Installing Win XP the old MBR will be overwriten.

---

### Post by The Kraken on 2011-12-13
But I cant install XP. It doesn't get past the initial set up. Heres the BSOD that I get.[IMG]http://techstroke.com/wp-content/uploads/2011/04/image_thumb6.png[/IMG]

---

### Post by BC59 on 2011-12-13
Go to these pages and read the troubleshooting actions: 

[http://support.microsoft.com/kb/324103](http://support.microsoft.com/kb/324103)
[http://support.microsoft.com/kb/316401](http://support.microsoft.com/kb/316401)

---

### Post by mips on 2011-12-13
[http://www.google.co.za/webhp?sourceid=chrome-instant&ie=UTF-8&ion=1#hl=en&cp=43&gs_id=14&xhr=t&q=STOP:+0x000007B+(0x80786b58,+0xc0000034,&pf=p&sclient=psy-ab&site=webhp&source=hp&pbx=1&oq=STOP:+0x000007B+(0x80786b58,+0xc0000034,+0x&aq=f&aqi=&aql=&gs_sm=&gs_upl=&bav=on.2,or.r_gc.r_pw.r_cp.,cf.osb&fp=f4a0661e2f00b683&ion=1&biw=1499&bih=841](http://www.google.co.za/webhp?sourceid=chrome-instant&ie=UTF-8&ion=1#hl=en&cp=43&gs_id=14&xhr=t&q=STOP:+0x000007B+(0x80786b58,+0xc0000034,&pf=p&sclient=psy-ab&site=webhp&source=hp&pbx=1&oq=STOP:+0x000007B+(0x80786b58,+0xc0000034,+0x&aq=f&aqi=&aql=&gs_sm=&gs_upl=&bav=on.2,or.r_gc.r_pw.r_cp.,cf.osb&fp=f4a0661e2f00b683&ion=1&biw=1499&bih=841)

---

### Post by aPockEllipse on 2011-12-15
> **The Kraken said:**
> 
For some reason it will install and run the  latest version of ubuntu but it will not let me install windows at all. I  get a blue screen of death. 

My question is how do i get around the bsod to install windows? what should i be looking for that would cause this to happen?

Also, i have another pc with windows on it. would it be possible to just  switch the hard drives? if so how much trouble could i expect to run  into?

In my limited experience doing this with windows 98se, it can work if donor and donee have same chipset. (perhaps similar chipset is good enough?)
if this was preinstalled (dell, acer...) windows, there might be a recovery partition, and maybe your friend burned recovery disks when first run (after purchase). Or is that windows install CD "full retail"?


I wonder if a bsod during install suggests severe hardware problem? Doesn't linux have badram adjustment? I don't know if this is automatic. Try a memory tester from a rescue/boot cd.

Also, isn't the usual multiboot recommendation to install windows first, then install your other OSes?

(just some brainstorming, or brainsqualling, or brainfog. whichever.)

(edited: remove "vista". :confused: I must have been reading a vista thread here.)

---

### Post by aPockEllipse on 2011-12-15
> **mips said:**
> [http://www.google.co.za/webhp?sourceid=chrome-instant&ie=UTF-8&ion=1#hl=en&cp=43&gs_id=14&xhr=t&q=STOP:+0x000007B+(0x80786b58,+0xc0000034,&pf=p&sclient=psy-ab&site=webhp&source=hp&pbx=1&oq=STOP:+0x000007B+(0x80786b58,+0xc0000034,+0x&aq=f&aqi=&aql=&gs_sm=&gs_upl=&bav=on.2,or.r_gc.r_pw.r_cp.,cf.osb&fp=f4a0661e2f00b683&ion=1&biw=1499&bih=841](http://www.google.co.za/webhp?sourceid=chrome-instant&ie=UTF-8&ion=1#hl=en&cp=43&gs_id=14&xhr=t&q=STOP:+0x000007B+(0x80786b58,+0xc0000034,&pf=p&sclient=psy-ab&site=webhp&source=hp&pbx=1&oq=STOP:+0x000007B+(0x80786b58,+0xc0000034,+0x&aq=f&aqi=&aql=&gs_sm=&gs_upl=&bav=on.2,or.r_gc.r_pw.r_cp.,cf.osb&fp=f4a0661e2f00b683&ion=1&biw=1499&bih=841)

I found this by chance, then focused the search on the complaint:
LX 6810-01 | 6810 ~predict | random power |dies | shutdown problem

[http://reviews.cnet.com/desktops/gateway-lx-6810-01/4852-3118_7-33513654.html](http://reviews.cnet.com/desktops/gateway-lx-6810-01/4852-3118_7-33513654.html)
____________

Be sure all fans in PC are running (PSU, CPU, video card, maybe case fan(s))

Also, try opening the side of the case, point a household fan into the case. then try installing. 
_________________
i also refined mips's search:
[solved | "thank you" | "that worked" | "it works" | "works now" STOP: 0x000007B (0x80786b58, 0xc0000034](http://www.google.com/search?q=solved+|+%22thank+you%22+|+%22that+worked%22+|+%22it+works%22+|+%22works+now%22+STOP:+0x000007B+(0x80786b58,+0xc0000034&as_qdr=all&num=100)

---

### Post by The Kraken on 2011-12-17
I want to thank everyone for all the help that they have provided me. I really appreciate it. I have gotten kind of lazy about getting this issue resolved, partly because I'm getting used to having Ubuntu run on this machine and am starting to use it more and more for my daily computing tasks.  I have decided to go ahead and keep Ubuntu installed and stop fiddling around with it. I have had to install/reinstall Ubuntu several times during this process and am getting tired of putting the programs that I like back on.

So, what I'm gonna do is keep Ubuntu installed and just save my pennies for another hard drive, or better yet a whole new computer. Again, thank you all so much for your efforts. I'm sure you will see me around the forums. Thank you.

---

