---
title: "Restoring XP"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by dRock1286 on 2007-04-24
Alright...I'm very happy with my current install of Ubuntu.  I use it on its own harddrive and have XP loaded on its own hard drive as well.  Now comes my question...

Over the years I have accumulated a lot of crap in XP.  It seems like it takes the computer about 10 minutes to completely boot up.  The computer itself is decent.  Runs on a 3.0 gHz P4, H/T, and a 200g hd.  On my 160G ubuntu drive, it takes under a minute (it seems) to boot.  I know there is something about less files to boot in Linux or something...I don't know.  So, I would like to restore my XP drive back to the bare minimum, basic defaults that it came with.  From there, add only free software.  But, will restoring the harddrive with HP's restore option on the BIOS screen mess up my install of Ubuntu?  I would, of course, disconnect the Linux drive but I want to make sure that it will still boot as normal like before.  Any help here?

---

### Post by mikewhatever on 2007-04-24
Reinstalling Windows on another HDD will, of cause, have no effect on Ubuntu, however, it may wipe GRUB out from the MBR, in case it is there. Do you know where is GRUB stage 1 installed? If not, check it like this:
> sudo grub
grub> find /boot/grub/stage1

You should get an answer like (hd0,1) or similar. If GRUB is on the same HDD with Ubuntu, there is nothing to worry about. If not, you'd have to reinstall it after having done with Windows.

---

### Post by oilchangeguy on 2007-04-24
if you disconnect the drive with ubuntu there should be no problems, other than you may have to reinstall grub.

---

### Post by dRock1286 on 2007-04-24
I'm in my windows right now, is there any way to check where GRUB is located in Windows?  I'm working on homework on a program that WINE doesn't handle...yet...and I can't reboot for Ubuntu right now...

---

### Post by deathbyswiftwind on 2007-04-24
If im not mistaken the "alternative" cd edition has a feature to restore grub. At least it did when dapper came out. Check into it Ive used it before.

---

### Post by umattu on 2007-04-24
If your worried about messing up grub or ubuntu or windows for that matter. Why dont you run msconfig and remove the tons of startup apps that have accumulated. Most apps installed in windows like to start them selves at boot, every new app is another lengthening the amount of time it takes to boot. This may not get you booting as fast as a fresh XP istall with no installed apps but it will speed boot times drasticly.



Go Start>Run

type msconfig hit enter

the tab on the left is startup, click it, you will see the paths to the apps. start unchecking the entries, on a fresh install there is not 1 app here so dont worry that you will mess up the OS, ( I recommend leaving the antivirus software to run at boot, for obvious reasons) everything else can go.

---

### Post by dRock1286 on 2007-04-24
> **umattu said:**
> If your worried about messing up grub or ubuntu or windows for that matter. Why dont you run msconfig and remove the tons of startup apps that have accumulated. Most apps installed in windows like to start them selves at boot, every new app is another lengthening the amount of time it takes to boot. This may not get you booting as fast as a fresh XP istall with no installed apps but it will speed boot times drasticly.


But I would like to just start over completely with it...

---

### Post by crav on 2007-04-24
I just went through this. I would highly recommend NOT using the HP restore disc. Get a windows disc (if you download one and use your current CD key, it's still legit) and install that, and get all your drivers from HP.com. This will prevent all the junkware that HP installs.

My HP "recovery discs" were 4x4.7gig DVDs. Windows is 1x700MB CD. Besides drivers, everything else on those discs is just slowing you down.

---

### Post by dRock1286 on 2007-04-24
Can I not just use the Restore option on the BIOS screen or is the windows cd plus finding drivers the best way to go?  Also, what drivers, generally speaking, will I need right off the bat?  I have a wireless card and wireless mouse but they both came with cds...anything else I will need?  Plus, how do I find my XP key?  Even though I don't care about being 'legit', if I paid for it, I might as well use it...

---

### Post by oilchangeguy on 2007-04-24
just use the built in restore option. what the previous post is talking about is all of the un-needed software thats pre-loaded on some low end machines. if that's the case with your computer. just remove any junk software. the restore software will probably include outdated virus software. remove this and go to [http://free.grisoft.com](http://free.grisoft.com) and download and install one of the better free anti-virus programs available. then visit [www.microsoft.com](www.microsoft.com) and download and install all available updates. use the custom setting, so you can view every update. also while at microsoft.com download and install windows defender, this is anti-spyware software.

---

### Post by tehbeermang on 2007-04-24
10 minute boot? That sounds like a case of Windows malware. 

First step: antivirus. Update it, run it. If you don't have it, get it. Avast is free for non-commercial use.

Second step: lavasoft ad-aware. Update it, run it.

If it still acts goofy, run ad-aware from safe mode, then again in a regular boot.

Third step: either use Firefox, Opera, or disable third party plugins within IE. IE's "Browser Helper Objects" (BHOs) makes it easy for malicious websites to hoist garbage into your hard drive. Either disable it or disown it.

Upgrading to IE7 reinstated the BHOs on my laptop. I've since disowned IE.

+3 for Linux.

---

### Post by dRock1286 on 2007-04-24
Antivirus, spyware, ad-ware...nothing.  I just have a lot of programs that boot at startup.  I want to just clean my harddrive off and start over...

---

### Post by oilchangeguy on 2007-04-24
read post #10

---

### Post by dRock1286 on 2007-04-24
Thanks.  I'll do this...I've just got to finish this homework first.  Thanks for all of your help, guys.

---

### Post by dRock1286 on 2007-05-01
Ok...so I have finished my class.  Now I want to restore my Windows Harddrive.  When I unplug my linux drive from my computer and try to load the windows drive, the grub loading screen still comes up.  Why?  What will happen when I restore my computer?  Will I also need to reinstall Linux or something else?  Any help would be nice   :D

---

### Post by teddybairs1 on 2007-05-01
If GRUB is still coming up, it means that your mbr is sitting on your windows hard disk. It also means that if you try to reformat the disk and reinstall windows you will wipe your ability to boot to Ubuntu.

I would recommend cleaning out your windows partition down to the bare minimum of programs using add/remove. Also, remove your anti-virus. If it's Norton or McAfee, these are basically just viruses or spyware themselves and most of the time these are what are causing your insanely slow boot time.

If you absolutely need an Anti-Virus, use AVG, it's non-intrusive and doesn't muck up your system like everything else does.

In general, don't bother using your Windows Partition to connect to the internet to begin with. It's asking for trouble. Use Ubuntu and you won't have to worry about mal-ware or hacking.

---

