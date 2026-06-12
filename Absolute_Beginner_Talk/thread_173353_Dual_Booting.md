---
title: "Dual Booting"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by DavidRanieri on 2006-05-10
Is it possible to run two hard drives one with windows xp pro and the the other with ubuntu?

Thank you for your assistance.

---

### Post by Sef on 2006-05-10
Yes, you can do it that way.

---

### Post by DavidRanieri on 2006-05-10
[QUOTE=Sef]Yes, you can do it that way.[/QUOTE]

Could you find time to write a small tutorial on how to accomplish this or email it.
I think there are some that would find this information useful

---

### Post by Sef on 2006-05-10
take a look at this

[http://www.linuxforums.org/forum/installation/42408-dual-boot-two-hard-drives.html]("http://www.linuxforums.org/forum/installation/42408-dual-boot-two-hard-drives.html")

---

### Post by Borniet on 2006-05-10
Quite some tutorials written about this already. Basically it is very simple. You have a pc with one HD with wind**** whatever on it. You crack open your pc, and plug in the second hd (make that the biggest one, you'll find yourself using Linux more then windows one day!!!). Power on PC, make sure HD is visible, throw in the Ubuntu CD, and boot it. When Ubuntu asks where to install, tell him to use the new HD. When the time has come to configure Grub (the bootmanager), the installer will ask you if you also want to boot other OS'es. It is safe to acknowledge this, and have it pointing to your old drive with Wind*** Whatever on it.
Now, when your PC reboots when the installation is finished, you will see a small menu, asking you which os to boot, Ubuntu, or Wind**** Whatever. This is the time of Truth, choose Ubuntu, and never look back again ;-)
Should you ever want to get rid of the Grub and Ubuntu thing: just throw in a Wind*** Whatever boot CD or diskette or pigeon (if you can find one you can boot from that is), go to the dos-prompt, and give the command 'fdisk /mbr'. Then start weeping because you just lost your precious...
BTW: If you have the option, always install windows first, then Linux, this is by far the easiest.

---

### Post by DavidRanieri on 2006-05-10
[QUOTE=Sef]take a look at this

[http://www.linuxforums.org/forum/installation/42408-dual-boot-two-hard-drives.html]("http://www.linuxforums.org/forum/installation/42408-dual-boot-two-hard-drives.html")[/QUOTE]

My thanks

---

### Post by richbarna on 2006-05-10
Basically you just install windows on one hard drive, then you install Ubuntu on the second hard drive. Ubuntu setup is automatic step by step. When GRUB asks where to put the master boot record MBR, make sure that it is placed where the windows MBR is on the windows drive, that way you get to choose both operating systems at boot.
I always use GRUB for dual booting and never have any problems.

What I have done, on an 80 Gig Drive, is 10 Gig for Xp 70 Gig for Ubuntu.
My second drive is a FAT 32 formatted 40 Gig that is accessible from both windows and Linux for storage (Music,Docs etc.)

---

### Post by DavidRanieri on 2006-05-10
[QUOTE=Borniet]Quite some tutorials written about this already. Basically it is very simple. You have a PC with one HD with wind**** whatever on it. You crack open your pc, and plug in the second HD (make that the biggest one, you'll find yourself using Linux more then windows one day!!!). Power on PC, make sure HD is visible, throw in the Ubuntu CD, and boot it. When Ubuntu asks where to install, tell him to use the new HD. When the time has come to configure Grub (the boot manager), the installer will ask you if you also want to boot other OS's. It is safe to acknowledge this, and have it pointing to your old drive with Wind*** Whatever on it.
Now, when your PC reboots when the installation is finished, you will see a small menu, asking you which OS to boot, Ubuntu, or Wind**** Whatever. This is the time of Truth, choose Ubuntu, and never look back again ;-)
Should you ever want to get rid of the Grub and Ubuntu thing: just throw in a Wind*** Whatever boot CD or diskette or pigeon (if you can find one you can boot from that is), go to the dos-prompt, and give the command 'fdisk /mbr'. Then start weeping because you just lost your precious...
BTW: If you have the option, always install windows first, then Linux, this is by far the easiest.[/QUOTE]

True enough plenty has been written about a lot of things however I find Ubuntu forums and users to be the most well written and knowledgeable from the website to the OS as a matter of fact the best and if all the linux distros had open source help many like me would have changed a long time ago. When you have 18 years of data no matter what OS was used change is not a thing of liking or not it is a matter of client log, financial data, billing and such. So it is easy to say change and don't look back if one is a child or gamer with no real intrinsic value but for a company moving 6 400 gig drives of data and a whole bunch of dat backup tapes well you do the math. Business does not stop to wait for a forum reply.
I thank you for your help and is much understandable.
As for using linux and not looking back.
1) Use debian
2) Built debian server
3) Now starting hopefully virtual/dedicated web hosting company with ubuntu as the backbone will see since debian is my preferred OS for that. Seems if I am correct Ubuntu is built on the Debian core.
P.S. Don't for get about drives using S.A.T.A. 

My thanks as always.

---

### Post by DavidRanieri on 2006-05-10
[QUOTE=richbarna]Basically you just install windows on one hard drive, then you install Ubuntu on the second hard drive. Ubuntu setup is automatic step by step. When GRUB asks where to put the master boot record MBR, make sure that it is placed where the windows MBR is on the windows drive, that way you get to choose both operating systems at boot.
I always use GRUB for dual booting and never have any problems.

What I have done, on an 80 Gig Drive, is 10 Gig for Xp 70 Gig for Ubuntu.
My second drive is a FAT 32 formatted 40 Gig that is accessible from both windows and Linux for storage (Music,Docs etc.)[/QUOTE]

Thank you kindly for the simple and concise reply. :)

---

### Post by Borniet on 2006-05-10
No worries, I am not a student, nor gamer, I am a pro photographer and webdesigner, and indeed, all my data is on my PC's. That's why I put my trust in Linux, not in Windows.
You are right, Ubuntu is one of the best documented Linuxes, and is indeed derived from the Debian system.
My appologies for my previous post, if it was a bit 'childish' perhaps, but the sun is shining, the children are at home, and in about 2 hours, I will go home and play with them. Life can be so simple, and yet so beautiful!
I hope all goes well with your Ubuntu. Should you have more questions, do post them here, or mail me ;-)

---

### Post by Borniet on 2006-05-10
[QUOTE=DavidRanieri]Thank you kindly for the simple and concise reply. :)[/QUOTE]
Now that was a direct attack to my posts!!! ;-)

---

### Post by richbarna on 2006-05-10
> Thank you kindly for the simple and concise reply. 

Er, Sorry, I like getting long replies to my posts, gives me something to read. :)

---

### Post by DavidRanieri on 2006-05-10
Okay I am sorry if I offended any one. I like long posts as well and yes sun is shinning and my work day is just starting and every one including thier parents are at me.
I hopefully can go the club later and do some laps in the pool shoot some pool and lift some weights for my partial paralysis. 
Thank you to all. 
I hopefully can do something to help. 
My hope is is use unbuntu/xammp server suite for linux distros and find a good control panel for webhosting and then put this in an easy to understand installtion tutorial for new users or users like myself who know a lot but have to think about the small things that I have forgotten. 
If anyone is interested in participating with this project please let me know. Please again accept my apologies.
;

David Ranieri

---

### Post by Borniet on 2006-05-10
Silence*

---

### Post by confused57 on 2006-05-10
Another, alternate method for dual boot, 2 hd's"

[http://www.ubuntuforums.org/showthread.php?t=120994](http://www.ubuntuforums.org/showthread.php?t=120994)

[http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper](http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper)

---

### Post by Omnios on 2006-05-10
I have been dual booting on two hard drives for over a year now and basicly installed Ubuntu pointed it to my second hard drive installed, installed grub and has worked well ever since. Also I resized my windows hard drive with a vfat partition that I use as my XP My DOcuments and as my Ubuntu DOcuments partion which works very well.

---

### Post by richbarna on 2006-05-10
> DavidRanieri:- Okay I am sorry if I offended any one. 
No offense taken at all, The good thing about this forum is the humour. 
Also, amongst all the technical questions and answers it's nice to see the odd light hearted fun threads, like "what are you listening to?" and "word association" etc.
I've used lots of forums, this one kicks butt !!

---

### Post by Borniet on 2006-05-10
[QUOTE=richbarna]No offense taken at all, The good thing about this forum is the humour. 
Also, amongst all the technical questions and answers it's nice to see the odd light hearted fun threads, like "what are you listening to?" and "word association" etc.
I've used lots of forums, this one kicks butt !![/QUOTE]

Indeed, no offense taken at all!
Humour is what this world needs...

---

