---
title: "Xp won't dualboot"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by jakhicks on 2007-08-31
Hey, Just started using Ubuntu in the last few days and followed numerous guides on how to dual-boot with xp, however after installing Ubuntu and restarting into grup, when i go down to windows xp and press enter the pc goes to the screen saying "starting up..." and doesn't move from there. Any ideas on  how i can solve this problem?

---

### Post by jnorthr on 2007-08-31
Have you actually installed ubuntu on your machine ? Turn off your machine. Turn it on again and start the boot process. Then go into ubuntu just to confirm it works. This way we can see if your install of ubuntu was successful. If grub offers you the choice to boot into XP then it is likely that you still have a partition that contains a good version of windows. Of course, you will have made copies of all your valuable data from XP before you installed ubuntu.  That was a wise thing to do, so now if you've lost XP you will still have backup copies.

---

### Post by alienexplorers on 2007-08-31
Which drive do you have windows on your primary or secondary.  Windows has a bit of a dislike of being put on the secondary drive.  There are ways around this I beleive.  Just try searching the forum if this is the problem.

---

### Post by jakhicks on 2007-08-31
Yeah Ubuntu is installed and working, I've been using it for a few hours. Luckily I had just backed up everything and formatted my drive just for the sake of linux experimentations. I'd been using knoppix for a long time before that, Ubuntu is just new to me. And Xp is on the primary Hd, 1st partition, I installed it mainly as from [http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu) if that helps.

---

### Post by ts51 on 2007-08-31
I have an idea! Do this!:
 
Go into to your BIOS. This varies from computer to computer but you usually get in by typing F12 or F2. Change the boot order so that your CD drive is first. Save and exit your BIOS. Put the Ubuntu Feisty Fawn CD into your computer and restart it. A screen will come up. Go through the menu so that you can use the Live CD. Once you see Ubuntu's theme and the desktop, you are in Ubuntu (it's not installed yet, just being run from the CD. It may be slow but it will be faster after the install). Go to the Gnome Partition Editor. (I don't know its exact location as I am in Windows on another Computer...)Resize your partitions so that you have 2: 1)Your windows partions and 2) unallocated space. Format the unallocated space to ext3 or ext2. Ok now you have to resize the ex2 partion. Make it so that you have 256mb of unallocated space. Format that to linux swap. Save your changes. For me, I had errors everytime but it did make the partitions and I was able to succesfully install Ubuntu in a dual boot situation. Now, go to your desktop and click install. Follow the procedures, selecting your ext2 or ext3 as the place to install Ubuntu. When it is done, restart the computer. You will soon see what is called the GRUB bootloader. It will give you so many seconds to select a OS before automatically selecting your default (in your case Ubuntu unless you change it). You will be able to go into Ubuntu or XP now. 
 
That's my mini dual booting guide. I always install Ubuntu that way. If that doesn't work, I would reccomend watching the Ubuntu videos on how to install, and it's not like watching that creeping bald guy that **tries** to teach computer illiterate people Windows, Office, Ebay etc; You can find them here: 
[http://screencasts.ubuntu.com/](http://screencasts.ubuntu.com/) 
 
They have guides from everything from printing to burning a .iso file. 
 
Good Luck!

---

### Post by ts51 on 2007-08-31
sorry i started posting before you responded...

---

### Post by ts51 on 2007-08-31
I'm sure someone will make use of it though.

---

### Post by jakhicks on 2007-08-31
yeah ill give it a go, thanks. Now i just need to get nvidia graphics drivers, amarok to play mp3's and acc's, vlc to play dvd's and then install k3b all without an internet connection to the pc i have running ubuntu... any volunteers?

---

### Post by ts51 on 2007-08-31
just download the .debs by using google to find them. Put them onto a flash drive and put the flash drive in your USB port. Double click the .debs and install them. For example:
 
google "amarok for ubuntu" or "amarok deb". 
 
Why are you not using an internet connect? Get a wireless router or something.

---

### Post by Lord Illidan on 2007-08-31
> **ts51 said:**
> just download the .debs by using google to find them. Put them onto a flash drive and put the flash drive in your USB port. Double click the .debs and install them. For example:
 
google "amarok for ubuntu" or "amarok deb". 
 
Why are you not using an internet connect? Get a wireless router or something.

I have to agree.. Internet connection is an integral part of Ubuntu, one would say..it is so useful.

---

### Post by ts51 on 2007-08-31
when i had no internet connection available before some guy sent me broadcom drivers, i thought ubuntu SUCKED... then i got on the net for the first time and I wondered why I ever used windows.

---

### Post by jakhicks on 2007-08-31
K, I'll go googleing, and the only reasons I don't have internet connection is because i cant afford a wireless router...and Ireland is horrible for anything beyond dial-up. *dies a little inside*. Thanks for the help though.

---

### Post by ts51 on 2007-08-31
sorry mate. i've seen some dial up routers out there though... and hear in the states a run of the mill router will cost you 50 usd. not too much.

---

