---
title: "Remove Linux From Ibook G4 Help!!!"
date: 2006-08-01
forum: Apple PPC Users
---

### Post by geekwithoutportfolio on 2006-08-01
Hello world, im a newbie at using both a mac and Ubuntu (linux). i have a a few problems i need help solving.

1. I installed ubuntu on my G4 and i want to delete it now as i want to put the original mac os x back on. Ive tried several methods to delete ubuntu from my mac but still haven't succeeded, i tried using a knoppix disk to boot the mac but ubuntu always loads and none of the disks is able to boot.

2. i dont have my original OSX disk so i borrowed a friends hoping itll help me wipe the harddive clean and re-install OSX but that doesnt work either i get an error.

what can i do??????????????????

---

### Post by drosophyllum on 2006-08-01
this is not well written, what do you mean, if you posted the exact error message perhaps it would help?

---

### Post by drosophyllum on 2006-08-01
ok, 
I think I can help, but refasing it would help me help you.

Boot the ubuntu install disk and open the gnome partitioner, then delete the disk and click aply (in the menu).

---

### Post by chasisaac on 2006-08-02
> **geekwithoutportfolio said:**
> Hello world, im a newbie at using both a mac and Ubuntu (linux). i have a a few problems i need help solving.

1. I installed ubuntu on my G4 and i want to delete it now as i want to put the original mac os x back on. Ive tried several methods to delete ubuntu from my mac but still haven't succeeded, i tried using a knoppix disk to boot the mac but ubuntu always loads and none of the disks is able to boot.

2. i dont have my original OSX disk so i borrowed a friends hoping itll help me wipe the harddive clean and re-install OSX but that doesnt work either i get an error.

what can i do??????????????????

Back up your hard drive use something like carbon copy cloner ([http://www.versiontracker.com/dyn/moreinfo/macosx/13260](http://www.versiontracker.com/dyn/moreinfo/macosx/13260)) and back up the macintosh portion. Boot from that disk. Use the disk utiltites and reformat the mac. Resotre from backup.

---

### Post by TheEye on 2006-08-04
i am a mac os x guru for years people have been comming to me with this problem what you need to do is a clean install. start the mac os x(panther or better) disk and click install (under ubuntu file manager) it will install a utility that will let you start 
Password from the disk by holding down the c key and when you restart the installer should give you the option of a clean install it will however wipe out all your files so backup ne thing you dont want to loose
~the Eye [www.theGuruart.co.nr](www.theGuruart.co.nr)  (<----check my fractal backgroundds out )

---

### Post by alexhrdr on 2007-08-05
It's funny that I might come across the same problem exactly one year after this thread was posted.  I need to uninstall Ubuntu on my ibook g4 because I can't run software for my job (CeltX).  I love Ubuntu but won't be able to use it until I get an x86 computer I think.  

I have the .dmg files for OS 10.4 install but I have them on a PC.  No Macs around I'm afraid...  I can't burn them onto CDs/DVDs (can I use either?) because Nero doesn't know what a .dmg is.  I searched around the forums today and found a post that advised me to simply change the .dmg to .iso and burn it.  I did and Ubuntu system "cannot mount volume" due to an "invalid mount option."  

I would like to do a full clean install wiping everything off my hard drive and having OS 10.4 back.  The problem is that I don't know how to do that.  I know this is an old thread, but I need help.  What should I do?  I don't have the original back up drives (they're in another country) but I suppose I could go to the Apple Store around here.  I have the .dmgs.  Any advice would be really great, thanks...

I never would have embarked on this experiment had someone over at CeltX told me that their Linux application didn't support PPC, but I guess I should have thought about that.

---

### Post by Auria on 2007-08-05
> **alexhrdr said:**
> 
I would like to do a full clean install wiping everything off my hard drive and having OS 10.4 back.  The problem is that I don't know how to do that.  I know this is an old thread, but I need help.  What should I do?  I don't have the original back up drives (they're in another country) but I suppose I could go to the Apple Store around here.  I have the .dmgs.  Any advice would be really great, thanks...


I'm not sure what dmgs you're talking about - to wipe your drive clean and reinstall and you need is an OS X installation disk

---

### Post by stmiller on 2007-08-05
> **geekwithoutportfolio said:**
>  Ive tried several methods to delete ubuntu from my mac but still haven't succeeded, i tried using a knoppix disk to boot the mac but ubuntu always loads and none of the disks is able to boot.


Knoppix is for PC hardware only.

Just put in an OS X install disc, boot the CD by holding down 'c'. Before starting the install, go to the Disk Utility at the top of the screen and remove all partitions. Create one partition for OS X, then start the OS X install.

---

