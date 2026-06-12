---
title: "Windows user needs help installing Ubuntu"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by BudaTx on 2006-11-20
After years of Windoze I downloaded, burned and ran the live cd (6.10)  What a cool, great, neat product! Wow, I even poked around and got it to see my DLink wireless pci card. Very cool!
System is AthlonXP 1.8ghz w/512mb, runs ok from the cd drive and I thought "Let me clik on the 'Install' on the desktop".  Went through the menus, all seemed fine.  It says 'Remove your disk and reboot', OK. Done.  Reboot...nothing.  It's like the hardrive is gone, kaput.  It'll reboot the LiveCD after 7 minutes of trying to find the harddrive -Houston..we got issues.  So I read, and read, I need GParted!! Got GParted, started, poked around, and quit.  Not point & clik and couldn't tell what I was supposed to do? (hda & ext2 are there, what now?) 
Now why my post says "..love to use (but can't?)
These are the kinds of things that make even a knowledgable user such as myself reformat and install Win2K. It'll install and run no problems. Not to mention, I tried all of the above on another AMD duron950 w/256mb and got the same (Yes Virginia, I did the same process twice expecting different outcomes)  Which brings me to... Why a windoze user got so close to using Linux, cliking 'Install' and then going backwards and installing Win2k. Oh, btw, my hdisk was unformatted at start, it was freshly wiped and fdisked as a large disk so it was ready for anything.  Ideas? Comments?  Another try with simple point & clik instructions?  Ubuntu is soooo promising; yet so far away. 
TomC

---

### Post by drphilngood on 2006-11-20
Try DLing & installing with the ¨Alternative" installer.  I´ve never had any luck with the live installer.

edit:
Here´s the [link]("http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/ubuntu-6.10-alternate-i386.iso").

---

### Post by zytsef on 2006-11-20
Sounds like GRUB didn't get installed. 

Your computer will check your hard drive's master boot record (MBR, a special section of the disk) for a boot loader that will in turn load the OS. Windows has one too, you'll notice if you've ever dual-booted two versions of windows. Ubuntu uses GRUB (GRand Unified Boot loader), and it sounds like it didn't get installed to the MBR. I hope that's enough to get you started.

If you want more help provide more information about the options you selected and exactly what your computer is doing. Might also relate to some BIOS settings...

---

### Post by Dusibello on 2006-11-20
been there and did that a week ago... hung in there, fought through a few issues, and now am in ubuntuland forever...

maybe try installing in text mode with the alternate cd? that worked for me when the livecd pretty much bombed on my desktop and laptop...

---

### Post by gn2 on 2006-11-20
> **BudaTx said:**
> After years of Windoze I downloaded, burned and ran the live cd (6.10)  What a cool, great, neat product! Wow, I even poked around and got it to see my DLink wireless pci card. Very cool!
System is AthlonXP 1.8ghz w/512mb, runs ok from the cd drive and I thought "Let me clik on the 'Install' on the desktop".  Went through the menus, all seemed fine.  It says 'Remove your disk and reboot', OK. Done.  Reboot...nothing.  It's like the hardrive is gone, kaput.  It'll reboot the LiveCD after 7 minutes of trying to find the harddrive -Houston..we got issues.  So I read, and read, I need GParted!! Got GParted, started, poked around, and quit.  Not point & clik and couldn't tell what I was supposed to do? (hda & ext2 are there, what now?) 
Now why my post says "..love to use (but can't?)
These are the kinds of things that make even a knowledgable user such as myself reformat and install Win2K. It'll install and run no problems. Not to mention, I tried all of the above on another AMD duron950 w/256mb and got the same (Yes Virginia, I did the same process twice expecting different outcomes)  Which brings me to... Why a windoze user got so close to using Linux, cliking 'Install' and then going backwards and installing Win2k. Oh, btw, my hdisk was unformatted at start, it was freshly wiped and fdisked as a large disk so it was ready for anything.  Ideas? Comments?  Another try with simple point & clik instructions?  Ubuntu is soooo promising; yet so far away. 
TomC

If it's simple point-and-click you want, try PCLinuxOS, it's much more user-friendly, and seems more advanced in many aspects in my opinion.

If you've got W2kPro, use it. Superb OS, faster than Xubuntu on my laptop, and less bloat than XP.

Ubuntu is good, but not as good as the hype would suggest, it can be a real P.I.T.A. to get everything running properly. 
Ubuntu's best feature is this very active forum. 
There's are reasons it's so active......

---

### Post by BudaTx on 2006-11-20
Thanks all. Drphilngood & dusibello, I used the alternate install and it went fine on sys. #2, ready to go.  The first sys. (where the hd 'went away' is giving me errors about mounting cd rom and such, but it seems I'll be able to 'force' it.  Bet it's because that's the system I used Gparted on and messed up the hdrv. 
gn2 - I also tried PClinuxOS this weekend, was looking at both Ubuntu and PClinuxOS and although PCLoS seemed faster, it didn't pick up the wireless dlink.  Sort of a toss-up and your comments about 'active boards' wasn't lost on me either as I perused the PCLoS forums and FAQ's Saturday.
Thanks all!!
TomC

---

### Post by adamkane on 2006-11-21
Ubuntu isn't for you. Ubuntu is for those looking for an affordable and less proprietary OS. Ubuntu is for the mass of humanity without access to a proprietary OS.

---

### Post by drphilngood on 2006-11-21
Glad one worked out for ya´ on one anyway, BudaTx and I hope you enjoy Ubuntu.
Have a good one!

---

### Post by scc4fun on 2006-11-21
> **BudaTx said:**
> After years of Windoze I downloaded, burned and ran the live cd (6.10)  What a cool, great, neat product! Wow, I even poked around and got it to see my DLink wireless pci card. Very cool!
System is AthlonXP 1.8ghz w/512mb, runs ok from the cd drive and I thought "Let me clik on the 'Install' on the desktop".  Went through the menus, all seemed fine.  It says 'Remove your disk and reboot', OK. Done.  Reboot...nothing.  It's like the hardrive is gone, kaput.  It'll reboot the LiveCD after 7 minutes of trying to find the harddrive -Houston..we got issues.  So I read, and read, I need GParted!! Got GParted, started, poked around, and quit.  Not point & clik and couldn't tell what I was supposed to do? (hda & ext2 are there, what now?) 
Now why my post says "..love to use (but can't?)
These are the kinds of things that make even a knowledgable user such as myself reformat and install Win2K. It'll install and run no problems. Not to mention, I tried all of the above on another AMD duron950 w/256mb and got the same (Yes Virginia, I did the same process twice expecting different outcomes)  Which brings me to... Why a windoze user got so close to using Linux, cliking 'Install' and then going backwards and installing Win2k. Oh, btw, my hdisk was unformatted at start, it was freshly wiped and fdisked as a large disk so it was ready for anything.  Ideas? Comments?  Another try with simple point & clik instructions?  Ubuntu is soooo promising; yet so far away. 
TomC
You may want to use the gparted live cd to repartition your hd if you have not already installed win2k. If you have already installed win2k you can use the Ubuntu cd (live cd or alternate installer) to set up your system as dual-boot (keep win2k by making its partition smaller and installing ubuntu on a different partition that you create with the free space).
If not then you'll want to repartition your hard drive.

---

### Post by BudaTx on 2006-11-21
scc4fun - I had blown away win2k, wanted to start fresh.  All is well with mach. # 1, y'all are Great! Helpful and Kind (except for the person who thinks Ubuntu is for poor people with no computers - ["Ubuntu is for the mass of humanity without access to a proprietary OS."]
On the 2machine I got a dbconf(?) error when using the textmode installer. End result is that it installed.  Now I'm wondering if there is a way to allow only access to certain programs so that, let's say, I'm using the sys in a library and I only want users to be able to use the internet and nothing else - Like group policy in windoze.  I know I'm probably jumping way ahead for my knowledge level with LinBuntu (hey, like that? just made it up:-)  but I would also like to build a live cd that allows only internet, openofc apps and printing. Like a UBCD but with Ubuntu.  I'll poke around the boards when I get a chance later. Thanks again, these few hours over 3 days have proven very productive (given that I'm supposedly a person who isn't looking for 'less affordable' and wants 'more proprietary' software).  
TomC

---

### Post by aysiu on 2006-11-23
Once John E stepped into the thread, it stopped being BudaTx's support thread and started becoming a "Linux isn't ready for the desktop" discussion thread, so I've moved that discussion to [a more appropriate place](http://ubuntuforums.org/showthread.php?p=1795910#post1795910), and I've retitled BudaTx's post, in case he's in need of more help.

---

