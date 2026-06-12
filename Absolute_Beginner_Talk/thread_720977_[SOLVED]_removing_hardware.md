---
title: "[SOLVED] removing hardware"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by bilijoe on 2008-03-10
I have UBUNTU 7.1 installed, and have been getting along just fine, with no real problems; I'm very impressed.  I do have one little sticking point though--I removed 2 cd/dvd drives from the system, and UBUNTU still seems to think they are there.  It won't mount them (because there is no media in the drive), but still seems to think they are physically there.  What do I do to correct this?  All the other hardware changes I have made since the install appear to have been correctly handled by UBUNTU, with no help from me.  Is there something fundamentally different about the handling of optical drives?  Am I going to run into this when I add and/or remove HDDs?  Thanks for any help you can give.

---

### Post by tzulberti on 2008-03-10
To remove optical and/or physical drives you should first umount them (right clic, umount). 
If you restart the pc the problem should go away.

---

### Post by bilijoe on 2008-03-11
Thanks, but that doesn't work--possibly because I had already removed the drives (without executing an "unmount"), and rebooted, but the situation is more complex than I originally thought.  After I had first removed the drives and rebooted, both drives still showed under "computer".  After reading your suggestion, I re-connected the drives and rebooted (expecting to execute "unmount" operations for both, reboot, and have the situation fixed).  However... after reconnecting the drives, only one of them showed up under "computer", though neither showed in the side pane to the left of the browse window.:confused:  Confused, I shut down, disconnected the drives again and rebooted.  Again (with no drives connected), both CD-ROM 1 and CD-ROM 2 showed up, both in the main window, and in the side pane.  Right clicking on the icon in the side pane showed a "remove" option, with the word "remove" grayed out, but with the minus sign to its left shown normally.  I clicked the minus sign, but nothing happened.  I prowled around a bit, and found listed under "properties" (right clicked on the icon in the main part of the window) that the owner was "root".  Ah-ha, I thought.  Log in as "root" and "remove" the devices.  No such luck!  When logged in as "root", both the word "remove" and the minus sign to its left were grayed out.  Also, under "properties", the owner was now listed as "unknown" instead of "root".  Knowing better than to play around while logged in as "root";), I shut down, rebooted, and came back in as myself.  I now have a consistent situation where, when the drives are NOT connected, they both show in the main "computer" window, and in the side pane.  When both are connected only one shows in the main window, and neither shows in the side pane.  In neither case, can I access either drive. Under "System/Preferences/Hardware Information", when the drives are connected, they show, with correct information for each--when they are NOT connected, they are absent from this display, but still show up under "computer".  So, what the Sam Hill is up with all this?  It seems the hardware manager knows the score, but the "computer" display now always shows incorrect information.  I am going to abandon this computer (to handle lesser tasks, running Windows 98--the only "safe" version of Windows I know of), and install UBUNTU on a much newer, more capable machine, so this question is soon to become academic, but I still want to know what's going on here, and how to fix it, as I may change/add/remove hardware on the new [permanent] UBUNTU machine (which will be my main working computer--so long Mr. Gates).  Can anyone explain this seemingly self contradictory condition to me, and tell me how to get UBUNTU to correctly [re]recognize what hardware (specifically the optical drives, as I don't seem to have had any trouble switching other hardware around) is actually connected?  I'd really appreciate a definitive answer to this conundrum.  It really bothers me that, even when logged in as "root", I couldn't get access to these drives to delete them from the system.  Thanks in advance to anyone who can enlighten me on this issue, and is willing to take the time to figure it out and explain it.

---

### Post by tzulberti on 2008-03-11
Sorry, but i don't knwo what is happening...:confused:

---

### Post by chewearn on 2008-03-11
Look into the file: /etc/fstab
You should see the cdroms listed in there.  Despite physically removing the cdrom, the entries in fstab are still present.

---

### Post by LeAstrale on 2008-03-11
> **AstalaVista said:**
> Look into the file: /etc/fstab
You should see the cdroms listed in there.  Despite physically removing the cdrom, the entries in fstab are still present.

i know this might seem irrelevant, but isnt there anything updating fstab normally ?

as far as your problem goes, are you sure that the jumpers on the cd drives are set correctly ?

/Astral-1

---

### Post by gobuntu on 2008-03-11
One reason why drives get "lost" somewhat as mentioned is that they are unpluged before unmounting.

When that happens, if no other better way, is to reformat the drive, plug it into and OFF system, and reboot.

It's happened to me with USB drive where I had backups, luckily they were backups that could be backed up.

Now, in some such case, the USB drive was formated for NTFS (Windows XP) and when the USB stick was in, Linux would not even boot. Removing the corrupted drive then Linux would boot.

With corrupted drives, two drive icons can show on the desktop.

It may be important what file-system you have in those drives, and HOW you formatted them to begin with, specially if they are NTFS drives, as using a third party Windows software to format it may have been part of the problem. If drive is NTFS, better if Window formats it. When I formatted the drive with that utiliity, at one time the drive was showing wrong values for both used and free space, till reformatted in Windows XP,  in this case.

If viable, then, consider reformatting.

Hope all goes well.

PS: One thing I don't recommend is doing a Linux installation with external drives (USB) plugged in. After installation, plug them in and Ubuntu will recognize them. That''s because I could not remove a drifve icon once from a fresh installation, and the drive would not access, no way.

---

### Post by bilijoe on 2008-03-11
Thanks to Altavista for cluing me into /etc/fstab.  I had to go in and manually edit the file (I commented out the lines that referred to the CD/DVD drives), but that has solved my problem.  In order to edit the fstab file, I had to log in as root, but I was then able to do it.  A standard word of warning:!:--anytime you log in as root, BE EXTREMELY CAREFUL WHAT YOU DO, and log out, and back in as yourself as soon as you are done doing whatever you had to do as root.

---

