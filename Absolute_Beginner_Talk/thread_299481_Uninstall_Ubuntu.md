---
title: "Uninstall Ubuntu"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by IndioBoi on 2006-11-14
[B]Now, don't tell me, I know there's no such thing as uninstalling an OS, I've read through dozens of answers to this very question and I have visited Mycrosoft's *"How to remove Linux"* and *"Hermazone"* too, but still I have some problems.
I have [COLOR="Red"]Ubuntu[/COLOR] and no other OS installed on my laptop, but I want to install Windows XP. I do have a Windows XP installation CD, I choose to boot from the CD but nothing will happen, Ubuntu will start automatically. 
What should I do?[/B]

---

### Post by Bachstelze on 2006-11-14
Are you quite sure your BIOS is properly configured to boot from the CD ?

---

### Post by Zerodegree on 2006-11-14
If it is asking you to hit a button to boot to CD and you are and then it is starting Ubuntu then it is not finding something it is able to boot from in the CD Drive.  I would check the disk to make sure nothing is wrong with the disk.  

If it looks ok  you can always go into the bios and change it to boot to the CD only and not choose the Harddrive at all.  Just make sure you change it back afterwards.

Bill

---

### Post by IndioBoi on 2006-11-14
[B]Thanks for asnwering. 
Thanks *HymnToLife*. I'm sure my BIOS is properly configured to boot from the CD, I've just checked again.
Thank you *Zerodegree*. The CD is working fine, I just tried it in another computer and it started nicely.
Bill, I just went into the BIOS and arranged the values so that the harddrive would be the last. But I don't know how to change it to boot from the CD [COLOR="Red"]*only*[/COLOR]. 
I appreciate it.[/B]

---

### Post by steven8 on 2006-11-14
I have a cd, cd-r and dvd drive.  I have found that some disks just plian refuse to boot from the cd, but will boot from the cd-r or dvd.  I have found that cd drives on laptops can be major finnicky.  My guess is that your cd drive just doesn't like the media.

---

### Post by confused57 on 2006-11-14
Windows doesn't recognize ext3, but I wouldn't think that would apply to the Windows install cd...you may want confirmation from someone that really knows, but you might be able to reformat the hard drive as FAT32 with the gparted live cd:
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

This is definitely a longshot idea, you'd probably want a 2nd opinion 'cause I don't know if it has anything whatsoever to do with the problems you're having.

Edit: Thanks for testing, steven8...I wasn't sure, like you said, it shouldn't matter what's on the hd for the Windows install cd to boot.

---

### Post by localuser on 2006-11-14
> **confused57 said:**
> you'd probably want a 2nd opinion 'cause I don't know if it has anything whatsoever to do with the problems you're having.

Sounds about right to me.  If the hard disk has no O/S then the system could certainly not be able to boot to it.

---

### Post by steven8 on 2006-11-14
I hadn't thought of that.  I'm going to try something. . .

---

### Post by steven8 on 2006-11-14
Okay, I hooked up my HDD that has only Ubuntu on it, and popped in my winXP set-up disk during boot.  It read from the disk just fine.  The disk in the cdrom won't care whats on the HDD.  It loads into ram.

I still think your cdrom just doesn't like that disk for whatever reason.  Do you know of anyone else with a windows set-up disk you could try just to see?

---

### Post by seijuro on 2006-11-14
you might also try making a copy of the cd with another system I had a problem with a plextor drive in my father-in-law's computer that it simply would not read his brand new norton av disc no matter what so I got my laptop out and made a copy of the disc and it read the copy just fine I have no clue why it wouldn't read the original but the copy worked flawlessly.

---

### Post by steven8 on 2006-11-14
Certain drives just do not like certain media.  I have no idea why.  I once thought that it was because I was creating a disc in xp, then trying to use it in a win98 system, but then I had trouble in the same system.

Try copying it to a different disk and see how that works.  When you make the copy, if you haven't done it before, and your software allows it, choose copy to harddrive first.  That way you won't have mismatching speed issues between the drives.

---

