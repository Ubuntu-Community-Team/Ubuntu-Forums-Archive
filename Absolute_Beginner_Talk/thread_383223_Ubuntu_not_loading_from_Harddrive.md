---
title: "Ubuntu not loading from Harddrive"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by Martin56 on 2007-03-13
I booted Ubuntu from the Live CD and installed it on my 500gb WD SATA Harddrive. When it asks me to take out my cd and press enter to reboot, i take out the cd, close the tray, press enter but nothing happens. I have waited at this screen for at least 15 minutes but nothing happened. I decided to manually reboot and try to get into Ubuntu from the hard drive. Nothing happens except a small line in the corner flashes on and off. 

My computer specs are:
Asus P4P800 motherboard
Intel 3.0Ghz P4 CPU
1Gb of Ram
Ati 9700 Pro videocard
WD5000AAKS SATA Harddrive which i am trying to boot Ubuntu from 

Any help would be greatly appreciated.

---

### Post by kittyhawk63 on 2007-03-13
Hi, I just wanted you to know that I am looking at your comments. I will be with you as soon as I think I may have a suggestion. Hold on, someone may beat me to it. 
kh

---

### Post by tgalati4 on 2007-03-13
I've had trouble with 500 GB Hitachi "DeathStars".  They sometimes need breaking in to work properly.  I can't speak for Western Digital, but perhaps it is a similar problem.  Did you try doing a security wipe (multiple writes) on the Ubuntu partition to make sure that the disk can read from the entire partition?  Sometimes this is needed to verify the drive surface on high capacity drives.  Use the Western Digital install utility or Ultimate Boot CD to exercise it.

Also run memtest overnight (or at least 10 pass cycles) to make sure your RAM is up to snuff.  Windows doesn't care about wonky hardware, but Ubuntu's reliability depends on hardware reliability.

Good luck and welcome to the community

---

### Post by kittyhawk63 on 2007-03-13
This may not mean anything. It may not be a common problem, but I had trouble when I closed the tray and pressed <enter>. It seems, at least in my case, that Ubuntu prefers to close the tray itself. Just press <enter>. It will also open the tray when it wants you to remove the CD. 

If you get help from more experienced helpers, listen to them. Each of us contributes until you find a solution. Don't give up easily.

---

### Post by kittyhawk63 on 2007-03-13
I'm off to bed. Not sure what time zone you are in. But there are people on this forum 24/7. I have always had all my questions answered. Just learn to be patient. It will be worth the wait in the end. Ubuntu is a great OS. It takes some learning, especially for newbies coming from Windows. You won't be sorry if you just give it a chance.
kh

---

### Post by Martin56 on 2007-03-13
I'm currently downloading the ultimate boot cd so i will try to wipe the drive a couple of times after. I'll also run the memory tests once i have the boot cd on a cd. I forgot to mention in my previous post that whilce loading from the ubuntu cd, if i do not change any options but just press enter to install, i get this error message regarding irq 169. It says something like Irq #169 Nobody Cared. It tells me to run with the irqpoll option so that is what im doing all the time now just to get into the desktop. I press F6 and add the line irqpoll to the end. This usually takes me to the desktop if nothing freezes.

---

