---
title: "Want to load Ubuntu ONLY on my ibook"
date: 2007-08-14
forum: Apple PPC Users
---

### Post by rooftoplounge on 2007-08-14
Is this possible? I don't have any mac OS cds, only the 7.02 Ubuntu cd mailed to me. I did some searching and was unable to find if this could be done without a mac OS or OS cd already installed to do a separate partition. Can anyone direct me to the right topic or is this not possible without having an initial mac OS?

I have a ibook G3 600mhz with 300 megs ram and a 20gig HD. The HD is formatted mac, but there's no OS on it. 

Thanks!

---

### Post by arijarot on 2007-08-14
> **rooftoplounge said:**
> Is this possible? I don't have any mac OS cds, only the 7.02 Ubuntu cd mailed to me. I did some searching and was unable to find if this could be done without a mac OS or OS cd already installed to do a separate partition. Can anyone direct me to the right topic or is this not possible without having an initial mac OS?

I have a ibook G3 600mhz with 300 megs ram and a 20gig HD. The HD is formatted mac, but there's no OS on it. 

Thanks!

I think that this a good link to look at [https://help.ubuntu.com/7.04/installation-guide/powerpc/pr01.html](https://help.ubuntu.com/7.04/installation-guide/powerpc/pr01.html)

---

### Post by creedog on 2007-08-14
Boot off of the cd and I think that you will be surprised. Hell, I first installed linux on a mac over a year ago, and I would assume that the install has only gotten easier.... I think that I was using ubuntu....but who knows....

Nontheless, its actually easier not to have Mac OS installed on a partition, that way you do not have to be careful not to overwrite it. Ubuntu disk will format the disk for you.

---

### Post by thevictor390 on 2007-08-14
Insert the CD, hold the "c" key while you boot it up, and you're installing Ubuntu.  Worked for me, anyway.

---

### Post by stmiller on 2007-08-15
If it's a new world mac (I think this one is?) then it can be 100% Linux. Old-world macs need a Mac partition to be able to boot.

There's some cut off of macs that became new world modes. Wikipedia has info I believe.

---

### Post by rooftoplounge on 2007-08-15
Hey there all,

Thank you for your responses, I tried booting from the cd by holding down "c" but all I keep getting is the blinking folder w/ the question mark. Do I have the wrong cd? Thanks again!

---

### Post by 3rdalbum on 2007-08-15
You say the Ubuntu 7.04 CD was mailed to you? Was it a CD that you requested from the Ubuntu website?

If so, then it only works on Intel and AMD-based computers. You'll need to download (or ask a local Mac User Group for) the version of Ubuntu for PowerPC computers.

You can download a disc image which can be burnt to disc from this URL: [https://wiki.ubuntu.com/PowerPCDownloads]("https://wiki.ubuntu.com/PowerPCDownloads")

---

### Post by rooftoplounge on 2007-08-16
Yes, I was trying to use the cd sent to me through the mail. I only have a PC connected to the internet with nero6, from my understanding I can't burn a mac-compatible boot disk with my pc, is that true?

If I had access to a mac would I just download and burn it or would I need to setup a specific format? 

Thanks everybody!

---

### Post by tgalati4 on 2007-08-16
Some older Mac CD readers would only take 650 MB disks.  So,  yes, it's possible if you are burning 700 MB disks on a PC then you may have trouble with a MAC.  However, I believe the G3 Macs have the newer style drives.

Be sure to burn the disks at a slow speed (4x) and check for data integrity afterward.

---

### Post by pxwpxw on 2007-08-16
Here are the files you see in the PPC and the i386 Desktop CD. The Alternate CD's have no casper folder. You can see this using your PC.

PPC-mac on left.           i386 on right has isolinux folder.

---

### Post by rooftoplounge on 2007-08-16
> **pxwpxw said:**
> Here are the files you see in the PPC and the i386 Desktop CD. The Alternate CD's have no casper folder. You can see this using your PC.

PPC-mac on left.           i386 on right has isolinux folder.

So it looks like I've got the pc version. Upon doing a little more research it looks like I can't burn a bootable cd with my pc, something to do with the incompatible iso format. crap.

I've sent a couple of emails to local mac user groups to see if they have a mac ppc version so hopefully they can get me going. Any other suggestions out there? You guys have been a major help, thanks!

---

### Post by supremedalek on 2007-08-17
If you get that desperate, pm me your address and I'll burn you a cd.

---

### Post by thevictor390 on 2007-08-17
Yes, you CAN burn a Mac CD just fine.  I did it myself, and got it working on three iBooks older than that (2 500 MHz models with 256 MB RAM, 1 300 MHz "clamshell" with 128 MB RAM).  Both booted from the CD just fine.

However, due to a problem with xorg, I would recommend getting the alternate install CD.  800 x 600 resolution is too low to install since the buttons are cut off, and until you're installed, you can't fix xorg.conf to work with 1024 x 768.  

Just note that if your iBook is like mine (which I think it is), then you will not have sound working, and there will be some video problems.  The video problems are easily fixed by reconfiguring xorg (there are plenty of topics on this) but I'm still working on sound.

Just make sure you get an alternate install cd.  you should be able to find one from the list in the FAQ sticky.  And BTW, I used UltraISO to burn it, so I can't tell you if Nero will work.

---

### Post by BryannMelvin on 2007-08-17
I don't think the c key will do. that's if Yaboot is installed I think


put the cd in and use the OPTION  key as you turn on power.

Note I had display problems with SEVERAL ubuntu cds. My current version is Feisty but I had to use the edgy alternate cd and then upgrade with the feisty alternate cd to avoid manually fixing the x.org setup.

I run Ubuntu only on Ibook g3 500  no Mac OS  so it definitely can be done. been doing this since Ubuntu5.04

---

### Post by thevictor390 on 2007-08-17
OK, "c" key will absolutely do it (although option may as well).  All three of the iBooks I've installed on used the "c" key to boot from CD.  Two had Mac OS X 10.2 installed, one Mac OS 9.2, so I don't think that matters either.

---

### Post by pxwpxw on 2007-08-18
> **rooftoplounge said:**
> So it looks like I've got the pc version. Upon doing a little more research it looks like I can't burn a bootable cd with my pc, something to do with the incompatible iso format. crap.


As you have a PC CD, and a PC, why not put a small ubuntu installation on the PC.
 Then it is very easy to make a USB flash stick network installer  using ubuntu on the PC, formatted to boot the Mac.

Download boot.img.gz from the current ppc netboot installer images. (its about 9MB)

if your usb stick is /dev/sdc
```

 sudo zcat boot.img.gz > /dev/sdc

```
boot from the mac open firmware
```

0> boot usb0/disk:,yaboot

```
That gets the install (or rescue)  started.
Tried it just now, using an ancient PC, checked booting on an iBookG4.

---

### Post by rooftoplounge on 2007-08-21
Success!!!! Thanks guys!!! 

So I downloaded activeiso burner1.1 for my pc, downloaded the ppc iso from the ubuntu website, burned the cd using activeiso (free program from cnet) and viola!! Ubuntu on my ibook! 

SO, it's running ubuntu "virtually" it hasn't actually installed onto the HD. It's displaying at 800x600 but it's leaving a section of black on the right-hand side, not filling the screen. I tried changing the settings but it won't display anything higher than 800x600, I also tried changing the "xconfig" in the terminal to select the correct monitor but I couldn't seem to get it to work, any advice? 

I also tried to install ubuntu onto the ibook itself but because of the resolution I can't see the "next" button in the "choosing my location" window, so i'm stuck. 

Thank you very much for all your help and I hope you can help some more!

*Edit* 

Ok, I neglected to READ "thevictor390" reply, so now I'm downloading the alternate cd so's I can install the version to correct the resolution problem. So unless someone has the code or can point me to the correct directions to change the xorg with the current version, I'll wait fer the alternate to download and give it a spin. Thanks again!

---

