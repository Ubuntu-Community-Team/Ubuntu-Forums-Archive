---
title: "Ide &amp; Sata"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by matolo on 2007-10-30
Hello.

I have decided to make the move on my primary machine from Windows to Linux, and I have chosen Gutsy to help get me re-acclimated to it.  For the most part everything is working fine, except for one major bump.

In the Windows environment, I used a 300 GB SATA HDD for my OS and most applications, and a 250 GB IDE HDD for storage.  My initial installation went through fine (installing to the SATA HDD), but when it came time to reboot, I discovered that it would fail; the Ubuntu splash screen would just hang.  I shut down, physically disconnected the IDE drive and booted again.  This time everything worked fine.  When I re-connect the IDE drive, it won't boot.

I am guessing that for some reason my computer wants to use the IDE HDD as the primary drive when it is connected (even though I've selected the SATA drive to be primary in the BIOS).  I'd love to get past this and migrate all the windows data I backed up to that drive.

Any help?  Please let me know if I can provide any technical information that may be of help.

Thanks!

MATOLO

---

### Post by ronald.higgins on 2007-10-30
Sounds familiar,

Had a similar issue and i had to set the BIOS to a specific option to see both the SATA and IDE drive, could it be PATA ? Anyway, i'll check my desktop BIOS Settings this evening and confirm if no-one has done already.

---

### Post by mdpalow on 2007-10-30
Just a thought...

You said you set the BIOS to boot from the HD, but did you set the BOOT ORDER of the two drives correctly? This is a different option in BIOS.

I don't know why this would be wrong since you obviously had it working with Windows before, but I'm not coming up with much else right now.

If all else fails and you're sure your bios is set right, you could always disconnect the IDE and do another quick and clean install of the OS. Then connect it back to the MB and see what happens. A clean install of Ubuntu 7.10 on your HD should only take about 10 minutes, so it might be worth trying real quick.

Good luck

---

### Post by matolo on 2007-10-30
> **mdpalow said:**
> Just a thought...

You said you set the BIOS to boot from the HD, but did you set the BOOT ORDER of the two drives correctly? This is a different option in BIOS.

I don't know why this would be wrong since you obviously had it working with Windows before, but I'm not coming up with much else right now.

If all else fails and you're sure your bios is set right, you could always disconnect the IDE and do another quick and clean install of the OS. Then connect it back to the MB and see what happens. A clean install of Ubuntu 7.10 on your HD should only take about 10 minutes, so it might be worth trying real quick.

Good luck

Thanks for the input mdpalow.

I did in fact try this...first, I installed with both drives connected, and after the initial reboot (after it prompts you to remove the liveCD) it failed to boot properly, so I shut down, disconnected the IDE drive and performed a clean install.  At that point everything was fine, but once I shut down and re-connect the IDE drive, it fails to boot again.  I've done this three times, just in case there was something I missed.

I also did adjust the boot order in the bios, to no avail.

Any other advice, anyone?

---

### Post by mdpalow on 2007-10-30
This is puzzeling. ](*,)

I can only make two more suggestions.

Shouldn't be a problem, but anything wrong with your HD jumpers in the back?

Lastly, maybe you could take the battery out of the Motherboard and reset the bios.

Very strange problem you have and it's even bugging me.

Oh, you could also install the OS to the IDE just to see how it acts. If it boots up then you know it's reading that IDE before anything else.

Good luck.. I'll check in later to see if you've had any success.

---

### Post by Pumalite on 2007-10-30
In some BIOS, you can go to IDE Configuration and set it to 'Enhanced Support for PATA+SATA' If that doesn't work, take a look at this link; it might provide some insight:
[http://ubuntuforums.org/showthread.php?t=567907](http://ubuntuforums.org/showthread.php?t=567907)

---

### Post by NT4usB on 2007-10-30
another place to look is fstab. Is it referencing the uuid of the drives?
(don't ask me what that means. I remember reading about problems with drives identified as HDA, etc. being fixed by using it's uuid to identify it.)

---

### Post by matolo on 2007-11-03
Well, I am happy to report that the problem has been resolved.  Unfortunately, I have no idea what I did to fix things! 

I disconnected and reconnected everything, re-installed, rebooted after removing the CD and everything was happy,  I was able to boot properly, and I can see my IDE drive (after manually adding it to /etc/fstab).  

But it brings up a related question: how can I get the IDE drive to automatically mount?  It doesn't initially appear under /media, To get it visible, I have to go to Places > Computer, then double-click on the IDE drive.  At that point, it asks for my password, and then an icon for it appears on my desktop, and I can browse via the file browser to the files contained within.  I can also at that point see it under /media.  

I also see that it is owned by root, and I cannot adjust the ownership or permissions on it.

Thanks for any additional help.

MATOLO

---

### Post by bluepowder7 on 2007-11-03
here's how to use ROOT powers to change the permissions of another drive that isn't directly under your /home folder.

[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

i had the exact same problem, and the above solution fixed it right up!  make sure you follow the Nautilus method, and you HAVE to make the changes from the folder manager view that is open and says "root" at the top - that's the only 'box' within which you actually get full root admin powers.

---

### Post by Pumalite on 2007-11-03
Or this:

Open a terminal and
Code:

sudo chown yourusername /whereveritismounted

---

### Post by matolo on 2007-11-03
> **Pumalite said:**
> Or this:

Open a terminal and
Code:

sudo chown yourusername /whereveritismounted

Thanks for that suggestion, Pumalite, but it remains owned by root.  
It's as if sudo is lacking it's normal abilities...

---

### Post by matolo on 2007-11-03
> **bluepowder7 said:**
> here's how to use ROOT powers to change the permissions of another drive that isn't directly under your /home folder.

[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

i had the exact same problem, and the above solution fixed it right up!  make sure you follow the Nautilus method, and you HAVE to make the changes from the folder manager view that is open and says "root" at the top - that's the only 'box' within which you actually get full root admin powers.

Ok I'm running Nautilus via gksudo, and I was able to graphically change the ownership to myself.  It ran for a bit, and then it was changed.  So, I closed Nautilus, opened a terminal and checked out /medis to see if the changes took.  Sure enough, the IDE drive was owned by root still!  

So, I still don't know how to have the drive automatically mount @ bootup, and the drive is still owned by root.  Bummer.

---

### Post by bluepowder7 on 2007-11-03
> **matolo said:**
> Ok I'm running Nautilus via gksudo, and I was able to graphically change the ownership to myself.  It ran for a bit, and then it was changed.  So, I closed Nautilus, opened a terminal and checked out /medis to see if the changes took.  Sure enough, the IDE drive was owned by root still!  

So, I still don't know how to have the drive automatically mount @ bootup, and the drive is still owned by root.  Bummer.

when i was doing it, i was being paranoid and changed all three options - top one for owner, middle for group, and bottom one for others, and set all 3 with "create and delete files" permissions in the 'folder access' field.  i also clicked the 'apply permissions to enclosed files' box for good measure.  that seems to have held on my machine quite well.  might be overkill, but it's my generic storage folder for all my docs, so i really absolutely needed to have full unrestricted access to it.

by the way, once i set the permissions, i closed the 'root' version of nautilus and did the remainder of my futzing around in the default user mode.

---

### Post by matolo on 2007-11-07
> **bluepowder7 said:**
> when i was doing it, i was being paranoid and changed all three options - top one for owner, middle for group, and bottom one for others, and set all 3 with "create and delete files" permissions in the 'folder access' field.  i also clicked the 'apply permissions to enclosed files' box for good measure.  that seems to have held on my machine quite well.  might be overkill, but it's my generic storage folder for all my docs, so i really absolutely needed to have full unrestricted access to it.

by the way, once i set the permissions, i closed the 'root' version of nautilus and did the remainder of my futzing around in the default user mode.

Thanks for the response, bluepowder.  Unfortunately, as soon as I select my user as the owner, it changes right back to root.

The oddest thing yet is, when I boot up initially, I cannot even find the drive in question unless I specifically point to Places > Computer.  That is the only location where I can even tell the drive is there.  It should be noted that if I open a Nautilus window (via gksudo or not), and I enter "computer:///" as the location (the exact same location as I get to via pointing to Places > Computer), I do not see the drive.  

Once I double-click on the drive, I am prompted to enter my root password, and then I can see everything on the drive as normal. 

SO, again, is there anyone who can help me figure this out?  It's kinda minor, I know, but it's driving me nuts!

Thanks to all who have helped so far, and for any future assistance.

MATOLO

---

