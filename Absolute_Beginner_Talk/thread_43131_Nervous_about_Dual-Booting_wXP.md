---
title: "Nervous about Dual-Booting w/XP"
date: 2005-06-20
forum: Absolute Beginner Talk
---

### Post by DavidF on 2005-06-20
I just got my Linux CDs in the mail, and was considering dual-booting it on my PC with XP... but I've read some horror stories here about XP not liking to dual-boot with Linux, so I am a bit nervous... moreso because I don't know where the XP CD that came with the PC is or the certificate, so if I need to reinstall XP, I will have to buy a full copy.

So, the question is, are the odds in my favor if I try the dual-boot, or is it a real gamble? And what pitfalls should I watch out for to keep it running well?

---

### Post by scourge on 2005-06-20
As long as you install Windows first and Linux second, there shouldn't be any problems. But if you have Linux already installed and you later install Windows, you won't be able to boot Linux anymore unless you restore Grub (there's a thread about it somewhere here).

So in short: no, there's no gamble, it will almost certainly work. Just make sure that you don't delete your Windows partition during the install process. It's also a good idea to install Grub (the bootloader) on MBR (master boot record), which is the default option.

---

### Post by DavidF on 2005-06-20
XP is already installed on this machine (the one I am typing on), so it's definitely the first OS installed.

I have Wednesday off, perhaps I'll install it then. But I'd still like to hear the opinions of others. :D

---

### Post by cwaldbieser on 2005-06-20
I have not yet had a problem setting up a dual boot WinXP/Ubuntu box.

Do you have a copy of the live CD, and does it work for you?  Specifically, if you run into trouble, can you access the web for help?

If you are really nervous, you could back up your master boot record and partition table.  This is useful to do even if you don't ever install Ubuntu.  The MBR usually doesn't get messed up, but if it ever did, you would be really glad you had backed it up!

---

### Post by DavidF on 2005-06-20
Yes, I have a live as well as install CD... I guess if worst comes to worst I could just format the entire HD and install only Ubuntu until I can get a new version of XP.

It's not the software install that bothers me... it's not having a "Plan B" if things go wrong, ya know?

---

### Post by mlindell on 2005-06-20
Another safe option, if you have two hard drives, is to keep Windows and Linux completely separate.  You can install Linux on the second drive and install GRUB on the boot partition of the second drive, keeping the master boot record on the Windows drive unchanged.  Instructions for such a setup can be found here:

[http://enterprise.linux.com/enterprise/05/02/16/1919205.shtml?tid=129&tid=49](http://enterprise.linux.com/enterprise/05/02/16/1919205.shtml?tid=129&tid=49)

Worked fine for me.

---

### Post by crane on 2005-06-20
I have installed Ubuntu repeatedly with now duel boot problems at all.

---

### Post by wake-kitty on 2005-06-21
i have winxp too and have been reinstalling ubuntu over and over with no problems at all. im a newbie in linux too and its worth the try  :)

---

### Post by TanKilleR on 2005-06-21
I had a horrer story, when I was very new to linux I did a dual-boot of xp/suse. And after I desided to remove suse I was never able to. So I ended up redoing my whole hdd. Keep in mind at the time I was minux stupid, so I did not know how to change hte GRUB back to the MRB. Also ubuntu forums are far more helpful than suse was, infact I dont think suse even offered one.

I'd say just ot be safe, use 2 hdds. One can get them super cheap on ebay. But thats just my option.

---

### Post by DavidF on 2005-06-21
[QUOTE=TanKilleR]I had a horrer story, when I was very new to linux I did a dual-boot of xp/suse. And after I desided to remove suse I was never able to. So I ended up redoing my whole hdd. Keep in mind at the time I was minux stupid, so I did not know how to change hte GRUB back to the MRB. Also ubuntu forums are far more helpful than suse was, infact I dont think suse even offered one.[/QUOTE]

That brings up another good question... I've read both that you **should** and that you **should not** put GRUB in the MBR... which is it?

---

### Post by aysiu on 2005-06-21
This is the difference. If you put grub on the master boot record, it takes over the boot record for your entire computer. That means your grub has to be configured to be able to boot both OSes (Windows and Linux). This is a *lot* easier to do, as most Linux distributions have installers that recognize Windows partitions and will automatically set up the dual-boot.

If you don't put grub on the MBR, grub will be only on your Linux partition. You then have to find some way to get Windows' boot.ini to recognize Linux. That means, usually, finding some way to copy the boot directory into some kind of .bin file (on a floppy) that then gets inserted into the boot.ini file in Windows c:/ directory.

If you don't know what you're doing, put it on the MBR.

---

### Post by Jole on 2005-06-21
Instaled the new Ubuntu and got no problems at all. The Grub boot loader instaled and found my windows installation as well.

Go ahead and Install Ubuntu. I recommend to you all  :grin:  :grin:

---

### Post by Spoofhound on 2005-06-21
[QUOTE=DavidF]

So, the question is, are the odds in my favor if I try the dual-boot, or is it a real gamble? And what pitfalls should I watch out for to keep it running well?[/QUOTE]

I've installed a few distributions in dual boot mode with no experience in doing this. I've settled on Ubuntu and have had no problems with a number of installs.

My advice is to have a look through these forums for some basic points regarding freeing up space in which to install Ubuntu (assuming its on the same hdd as XP), and how to follow the install instructions when you boot the cd. There are plenty of threads. Having done a bit of homework here I found the process straightforward and the installer did its job really well. A bit of reading, a basic plan, a deep breath and pretty soon you'll be wondering what all the fuss was about

---

### Post by Sliced on 2005-06-21
[QUOTE=Spoofhound]My advice is to have a look through these forums for some basic points regarding freeing up space in which to install Ubuntu (assuming its on the same hdd as XP), and how to follow the install instructions when you boot the cd. There are plenty of threads. Having done a bit of homework here I found the process straightforward and the installer did its job really well. A bit of reading, a basic plan, a deep breath and pretty soon you'll be wondering what all the fuss was about[/QUOTE] I agree with this completely.  I started a dual-boot project yesterday and accidentally wiped out my WinXP partition (note to all: NTFS needs to stay as NTFS, don't try and switch it to a different format).  If I had studied how to partition my HDD properly, I wouldn't be having the problems I'm having!

On another note, reinstalling XP has been a lot more problematic than Ubuntu, which is completely effortless.

---

### Post by davahmet on 2005-06-21
[QUOTE=Sliced]
On another note, reinstalling XP has been a lot more problematic than Ubuntu, which is effortless completely effortless.[/QUOTE]

I've said before, if users had to suffer through a Windows installation and configuration instead of having it pre-loaded, the predominate belief about Windows would be,"Isn't that just some clunky version of Linspire?"  ;-)

---

### Post by DavidF on 2005-06-21
[QUOTE=Sliced]On another note, reinstalling XP has been a lot more problematic than Ubuntu, which is completely effortless.[/QUOTE]

Well, as I think I said before, if worst comes to worst, I can just stick with Ubuntu until I can get the $$$ to replace XP... or, on second thought, since MS wants $200 for a full install of XP, and Dell only wants $300 for a new PC with XP already installed, I might just make this beast totally Linux and get a new Dell if things go wrong... maybe even if they don't! :D

---

### Post by Kapre on 2005-06-21
[QUOTE=DavidF]Well, as I think I said before, if worst comes to worst, I can just stick with Ubuntu until I can get the $$$ to replace XP... or, on second thought, since MS wants $200 for a full install of XP, and Dell only wants $300 for a new PC with XP already installed, I might just make this beast totally Linux and get a new Dell if things go wrong... maybe even if they don't! :D[/QUOTE]
 DavidF - I'm also a noobie and is now a month old using Ubuntu (D' BEST distro). I have a dual boot with my XPPro (but XP is now monthballed - I havent used it since I install Ubuntu). Also, I re-installed Ubuntu 2 times and my XP was not damaged/touched by the install and re-install.

Hope next time you post in the forum, you'll be using Ubuntu Linux.

Kapre

---

### Post by DavidF on 2005-06-21
Heh... well, maybe not the NEXT time, but I have tomorrow off, so trying the install is on my short list of things to do. :)

---

