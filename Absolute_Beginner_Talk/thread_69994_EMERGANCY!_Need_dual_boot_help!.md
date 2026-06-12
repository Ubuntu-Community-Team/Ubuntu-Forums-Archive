---
title: "EMERGANCY! Need dual boot help!"
date: 2005-09-28
forum: Absolute Beginner Talk
---

### Post by elemental_silver on 2005-09-28
Hurry hurry, I tried to dual boot Kubuntu and the boot loader is telling me "Filesystem type unknown, partition type 0x7" when I try to boot Windows XP Home. Its using NTFS file system. I NEED THIS FIXED ASAP, sorry for the rush but it's URGENT!

---

### Post by aysiu on 2005-09-28
If it's really that urgent, follow these instructions:

[http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkd_tro_ldau.asp](http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkd_tro_ldau.asp)

The instructions will mess up your boot loader so that you can't boot to Kubuntu any more--though, that can be fixed, too, eventually... after the emergency is over.

---

### Post by elemental_silver on 2005-09-28
Thanks, and yeah, its a super emergancy. Like "report due in hours" emergancy. I'm going to try this. Thanks, and please, everyone else, keep posting suggestions.

---

### Post by az on 2005-09-28
What do you need to report?

---

### Post by elemental_silver on 2005-09-28
I have a report I need to turn in to english in less than 12 hours and I need the solution for my problem so I can print it out >_<

Edit: Please please please, help. ;_;

Reedit: Progress, now I get an Error29: Disk Write Error

---

### Post by matthewv on 2005-09-28
What's wrong with using Kubuntu for your report??

---

### Post by Mustard on 2005-09-28
[QUOTE=matthewv]What's wrong with using Kubuntu for your report??[/QUOTE]
I'm guessing the report is on the XP partition.

---

### Post by matthewv on 2005-09-28
[QUOTE=Mustard]I'm guessing the report is on the XP partition.[/QUOTE]

I guessed the same, but its no drama to mount an NTFS partition under kubuntu/ubuntu.

---

### Post by j.hill on 2005-09-28
> I guessed the same, but its no drama to mount an NTFS partition under kubuntu/ubuntu.

How do you do it?  I heard somewhere that it couldn't be done, so I never tried.

---

### Post by Kyral on 2005-09-28
Linux can *read* NTFS fine. Linux *writing* to NTFS is completely another beast

---

### Post by matthewv on 2005-09-28
[QUOTE=j.hill]How do you do it?  I heard somewhere that it couldn't be done, so I never tried.[/QUOTE]
Like Kyral said, mounting NTFS read-only is no problem. You should be able to use that to at least access your report, and save your changes to your linux partition. To mount NTFS, have a read of [this]("http://ubuntuguide.org/#automountntfs"). These instructions will mount your ntfs at boot time, read-only. Hope it helps.

---

### Post by JimmyBEng on 2005-09-28
To j.hill
reading from (not writing to) NTFS is no prob, I've done it a lot.  just check here in the guide. [http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)
To elemental
hope everything works(or worked) out.  if you can't troubleshoot GRUB at the momment, try mounting your NTFS partition for reading and printing in Ubuntu follow link above for how to mount the NTFS.

---

### Post by aysiu on 2005-09-28
I would definitely recommend (now that I know what the emergency is) doing the manual mount of NTFS rather than doing the FIXMBR.

Just follow these directions exactly:

[http://www.ubuntuguide.org/#mountunmountntfs](http://www.ubuntuguide.org/#mountunmountntfs)

If you want to find out whether your Windows partition is really /dev/hda1 (it probably is, but you should be sure), type into a terminal ```
sudo fdisk -l
```

---

### Post by elemental_silver on 2005-09-29
Well, sadly, the responses were too late. I was forced to just clean format it all and write the report AGAIN. Sorry for not clarifying why I needed windows, but the reports in my english class must be in Word format, and I didn't want to risk turning in my report and get a 0 cause he can't open it cause Open Office made it. I'm going to try to install again, but I would really appreciate a walkthrough on this so it doesn't happen again.

---

### Post by matthewv on 2005-09-29
OpenOffice can save into Word format and import/export it, no problems.

With regards to reinstalling, if your computer has a floppy drive I would install the bootloader to floppy, so that no matter what removing the floppy will just boot you straight into windows. Just press No when asked to install grub to the mbr, stick in a floppy, and tell grub to install to /dev/fd0  That should install grub to your floppy, so, as long as you can boot off the floppy, you can get into Kubuntu/Ubuntu. Remove the floppy, restart, and you're in windows.

---

### Post by elemental_silver on 2005-09-29
Problem, no floppy drive. Installing on a new laptop. Time to invest in a thumb drive then...

---

### Post by aysiu on 2005-09-29
[QUOTE=elemental_silver]Problem, no floppy drive. Installing on a new laptop. Time to invest in a thumb drive then...[/QUOTE] Considering your ignorance about OpenOffice (and *ignorance* here is not meant as an insult--just an observation), I would hold off on installing Ubuntu. It has a nice live CD that does absolutely no damage to your hard drive. Play around with the live CD--get to know the programs and the general feel and workings of Linux. If it's still something you want to pursue and have *time* to pursue (don't install it a few hours before you have an assignment do... and definitely back up all your work before installing anything on your hard drive), then go for it after you've played around with the live CD.

Everyone here will be super supportive and helpful if you have specific questions and the time to work out different solutions. Also, as you may have learned from this thread--always give as many details as you can. Rather than saying, "Emergency. I need to boot into Windows!" you would have been much better off saying, "I set up a dual-boot, but, for some reason, I can't boot into Windows. I have an assignment I typed in Windows using Word, and I need that assignment. Is there any way I can get that assignment back short of reformatting the hard drive?"

Well... 20/20 hindsight, of course.

---

### Post by matthewv on 2005-09-29
[QUOTE=elemental_silver]Problem, no floppy drive. Installing on a new laptop. Time to invest in a thumb drive then...[/QUOTE]

I don't know (never tried it) but can the ubuntu installer work with a usb device, or install the boot loader to it???

---

### Post by elemental_silver on 2005-09-29
Ouch, kinda harsh even though you tried to place your words softly... I figured that my business was my own and that maybe some people out there could understand an emergancy situation like it was and perhaps not give me too much hastle about it. I appreciate those who helped without asking too much about it, that's the trademark of a true professional attitude, imho. And the individuals that did ask about my problem, I wouldn't have said it if I wasn't comfortable saying it. And for the individual that decided that he must remind me of my stupidity underhandedly, I apologize that my ignorance has caused you to waste so much effort as to write me about my own problems.

By the way, I do believe that this is the newbie forum. It wouldn't take much to deduce that I don't know much about Linux.

---

### Post by matthewv on 2005-09-29
Why not just try the windows version of OpenOffice.org (get the preview/beta version from [http://www.openoffice.org/]("http://www.openoffice.org/") and get used to openoffice, before trying out the ubuntu live cd and eventually, if you like ubuntu, installing to hdd?

---

### Post by elemental_silver on 2005-09-29
Because I like ubuntu, and I'm installing it as part of a personal project. I work for a small business that sets up and maintains networks. We're considering a serious leap of going into Linux networks, and I'm the monkey to train. Once I learn the in's and out's, I'll be expected to teach it to all the rest of my staff X_x

---

### Post by aysiu on 2005-09-29
[QUOTE=elemental_silver]
By the way, I do believe that this is the newbie forum. It wouldn't take much to deduce that I don't know much about Linux.[/QUOTE] No problem with that. Unfortunately, we who are trying to help (by the way, everyone here is just another Ubuntu user--we are not "professionals") need newbies who can ask questions. Rather than assuming OpenOffice would not be able to work with your Word document, you could have asked: "Hey, if I use a Linux app to save my Word document, won't that mean I can't access it in Windows?"

I'm just offering advice for the future. It's obviously too late now. We're not mind-readers. We don't know what your situation is and can help only about as much as we know. Take it as an insult if you want, but I think you'll find I can be just as helpful as anyone around here if given the chance.

In fact, I was the first one to rush to help you at the beginning of this thread, if you didn't notice...

---

