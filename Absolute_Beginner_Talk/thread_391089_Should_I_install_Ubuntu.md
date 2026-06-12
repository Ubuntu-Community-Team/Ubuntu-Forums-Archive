---
title: "Should I install Ubuntu?"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by shamushand on 2007-03-22
Greetings all!

I've been considering installing Ubuntu on my PC, but I'm not sure if I should. I have no experience with Linux, and I most absolutely don't want to harm my computer. I'm using a Dell Dimension B110 (barely 8 months old) and I have two HD's, one (C) with 80 GB running Windows Vista Home Premium, and one (E) with 20 GB with no OS, which is were I want to install Ubuntu. I have 1.27 RAM and a nVidia GeForce FX 5200 graphics card. 

I have read LOTS of stories about people installing Ubuntu then being unable to boot to Vista again. I don't know if this also applies to people with multiple HD's... If I do decide to install, will I absolutely 100% be able to boot to Vista? I use VistaBootPRO 3.1 to edit boot menu. And lastly, if something goes wrong during the install, will I lose files or have to format the Vista C: drive as well? 

I'm not installing Ubuntu if the C: drive won't be 100% safe...  :confused:

---

### Post by annda on 2007-03-22
i would suggest you wait a while, until more adventurous people have cleared the path.

however (especially if you install on another HDD) ubuntu will not harm your windows partition. the bootloader(s) can be a problem - or some issues with conflicting GRUB (linux) and vista.

here is some reading material:
[http://ubuntuforums.org/showthread.php?t=389250](http://ubuntuforums.org/showthread.php?t=389250)
[http://ubuntuforums.org/showthread.php?t=388756](http://ubuntuforums.org/showthread.php?t=388756)

i have absolutely no experience with vista, but from what i read, microsoft took extra precautions to make OS hopping more diffiicult. i'd say use use the live CD or vmware player and fall in love with linux/ubuntu, and forget what may happen to vista. but i know, it's not for everyone. 

one way or the other, have fun!

---

### Post by mikewhatever on 2007-03-22
All of your concerns have some ground, but if you really do not want to harm the computer, unplug it and put into the cupboard. Even then it is still in danger of getting dusty :).
Seriously now. Are you happy with Vista/XP? Do you only want to try Ubuntu because some friends have? If so, don't install. You'll have to learn by trial and error, get frustrated at times, certain things may not work, your posts may not be answered, etc.

---

### Post by Apostata on 2007-03-22
If you want to take a first step, why not download and try the Live CD of Ubuntu (or it's Windows-GUI-friendly cousin, Kubuntu). With a Live CD you can at least give it a road test without installing anything to your hard drive - if you like it, maybe you'll be more motivated to install and take the next step.

---

### Post by UpsideDownFace on 2007-03-22
If you have a second hard drive with nothing on it then there is almost nothing to go wrong.
Just answer the question of which disk/partition do you want it installed on, with the number of the second disk.
An excellent book is "The Official Ubuntu Book" ISBN 9 780132 435949.
This has a live disk (Ubuntu 6.06LTS) when I bought the book for about GBP 20, ( USD 35)

---

### Post by WiFi Ed on 2007-03-22
I'm triple-booting XP, Vista and Ubuntu without problems.:) 

 XP and Vista live on the C drive (one partition for each OS, C and D), Ubuntu lives on a second hard drive in one big partition (E).

I installed XP first, then Vista. Vista's bootloader gave me the choice of either OS.

Next, I booted my pc to the Ubuntu Live CD and after it loaded and I confirmed that it detected all my hardware and everything worked (video card, sound, Ethernet, etc.) I clicked on the Install icon on the desktop and followed the instructions step by step.

Being new to Linux, the nomenclature for the hard drives was confusing at first (C: and D: became "sda0" and "sda1" as I recall, and E: became "sdb0" or "sdb1") but I thought about what I was doing before just clicking on stuff. Ubuntu's partitioning tool asked me to make choices about where to put Ubuntu, partition sizes, file system types, etc. and then showed me that it would load  Ubuntu's bootloader (GRUB) on "hd0" (which was the C: drive).

I let the installation proceed and when all was done the pc was re-booted. A boot menu came up first with the choice of Ubuntu or "Longhorn" (Vista). Choosing Longhorn gave me the Vista bootloader with Vista or XP choices. Both worked just fine.

I re-booted after verifying the Windows stuff still worked and let the pc boot into Ubuntu. It also worked just fine.

If you're really paranoid, (I mean cautious) get a Vista-capable disk imaging application (Acronis True Image is nice, 30 day free trial) and image your Vista installation before installing Ubuntu. That way you can restore your Vista installation if something goes wrong.

I really like Ubuntu, and use it most of the time now.

Check out the links suggested in previous posts and google "Vista and Ubuntu dual-boot" for lots of tips...

---

### Post by shamushand on 2007-03-22
Thanks guys!


You see, the reason I'm being so "paranoid" is because if anything gets wrecked on the PC, it takes all day to restore it, re-install Vista, reinstall ALL hardware, programs, and get online again. During time, which, I have my parents scolding me because I was careless. :lolflag:

---

### Post by stijngysemans on 2007-03-22
maybe you can take an image of your current vista configuration, in case anything goes wrong?

---

### Post by euler_fan on 2007-03-22
I don't have Vista, so I haven't tried dual booting with it, but with XP, I do a clean re-install (after backing everything up, etc) of XP, install the minimums (AV, drivers, etc to get a working OS) and then pop in the liveCD and use it's built in installer. It asks me how much of the hard-drive I want to automatically give it (I usually pick about 65-75%, but I use linux primarily), and then it does the rest.

I have had no problems with GRUB, as it is quite intelligent. However, if you want to be extra safe, wait another 6 months (?) or so until a bunch of people have done dual boot with vista and then check again.

Good luck! If you choose to do this, you may want to take some good notes and post them, as I am sure others will want to read about your experience (good or bad).

---

### Post by shamushand on 2007-03-29
Well... after a disastrous attempt to Dual-Boot XP and Vista, I decided to use Virtual PC 2007 to run Ubuntu 6.10. I can now run Vista and Ubuntu at the same time, and I'm loving this! Now to install Beryl... Well, I'll do that this weekend. :)

---

