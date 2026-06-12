---
title: "Deleting Read-only files in a Windows Drive"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by blore123 on 2007-01-15
Hi,

I have some Spyware on Windows that I was never able to delete due to access restrictions (the program is always running as it's in the registry to start with the OS).

I thought hey, if I link it to my Ubuntu machine as hdb then it won't be running anymore!

Great plan in practise, I have the files waiting to be crushed! One issue though, anyone know howto delete a file marked as 'Read-only' it seems only root can change the status of the file and I do not know howto do this in terminal.

Would *really* appreciate a response to this...

:)

---

### Post by adewale on 2007-01-15
sudo rm filename

---

### Post by Canis familiaris on 2007-01-15
Is it an ntfs drive? If yes, you have to install ntfs-3g
Refer to this thread:
[http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs]("http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs")
Now in terminal:
in GNOME:
sudo nautilus /

in KDE: 
sudo konqueror /

scroll to the mounted folder and delete the spy 8)

---

### Post by Canis familiaris on 2007-01-15
Another simpler suggestion is to use Knoppix Live CD, mount your partition and simply delete the spy!

---

### Post by blore123 on 2007-01-15
Great! At least I now have a GUI method to access the NTFS volume (terminal is not as fast).

Problem is, I still cannot deal with the read-only nature of the mounted volume. So all files on it cannot be altered in any way!

Help!

---

### Post by Frank Golden on 2007-01-15
> **Anurag_panda said:**
> Another simpler suggestion is to use Knoppix Live CD, mount your partition and simply delete the spy!
Have you tried booting XP into "safe mode". Run a anti spyware program like Spyware Search & Destroy or Lavasoft's Ad-aware from "safe mode". Just hit F8 during post
to enter "safe mode".

Simply removing the offending spyware may cause errors if not done correctly.
For instance removing the executable can cause problems if the registry has an entry
calling for the spyware to be started with windows and the .exe isn't there anymore,
up to and including boot problems. Spyware peddlers should be shot.

A great little free program for Windoze is "startup CP" and the related "startup Monitor"
from Mike Lin

[http://www.mlin.net/StartupCPL.shtml](http://www.mlin.net/StartupCPL.shtml)

When downloaded and installed Startup CP places an item in your Control Panel that shows all the stuff on your XP install that starts up with Windows. From Startup CP you can uncheck programs you don't want to start up with Windows.
Startup Monitor monitors your system and warns you with a popup when a program tries
to modify the registry by registering an .exe to run at startup. It allows you to choose to allow this or not.

Sorry if I offended anyone with this M$ stuff.
But since this is a question about M$ spyware removal.......

---

### Post by blore123 on 2007-01-15
Hi,

I'm *way* past removal stage!

I've used removal and blocking software on it and it does nothing to this, now WinXP grinds to a halt - rebooting after 10 mins. I just want it off there.

If I have to say 'ok' on a few file not found warnings on bootup - I don't care!

---

### Post by blore123 on 2007-01-15
Ok, I've used your tool StartupCP and will now desist trying to defile a Linux Forum with questions about deleting NTFS files under Linux for Spyware handling.

I might point out though, the spyware attempts to add itself again to the program list when disabled or deleted.

Spyware peddlers aren't worth the bullet. They should be publicly sterilised and their children should be deported to Chernobyl or someplace they'll find it harder to reproduce properly to eradicate this.

---

### Post by Frank Golden on 2007-01-15
> **blore123 said:**
> Ok, I've used your tool StartupCP and will now desist trying to defile a Linux Forum with questions about deleting NTFS files under Linux for Spyware handling.

I might point out though, the spyware attempts to add itself again to the program list when disabled or deleted.

Spyware peddlers aren't worth the bullet. They should be publicly sterilised and their children should be deported to Chernobyl or someplace they'll find it harder to reproduce properly to eradicate this.
Have you considered backing up your data and reinstalling XP. This will temporarilly mess up grub if you are dual booting but you can restore grub fairly easily.
Don't worry about "defiling" this forum with XP, NTFS questions, many of us here are dual boot users, and enjoy a challenge.

---

### Post by blore123 on 2007-01-15
Here's where the fun begins...

Spyware is only properly removed by one method in my opinion - HDD format. Trouble is, I have no CD of WinXP (OEM installation) - I have a red floppy that points to a NON_DOS partition full of .cabs!

Trouble is said floppy is a Win98 recovery, not WinXP, so I'm worried about that a bit, and I have no DVD-RW (only CD-RW) to backup with, and my HDD is 72.5Gb full. That's going to be lot of lost time if this fails because my recovery disk is duff.

My WinXP isn't dual booting, so Grub won't be touched, WinXP's on another HDD that I smply swap the ATA cable over for when needed. I tolerated the loss of system speed in XP upto now because I'm patient, but shutting on me randomly just down isn't nice...

What I need is a Windows XP CD without the hassle of M$ anti-piracy warnings appearing on my PC, I paid for it afterall, so where's my disk!

---

### Post by Frank Golden on 2007-01-15
> **blore123 said:**
> Here's where the fun begins...

Spyware is only properly removed by one method in my opinion - HDD format. Trouble is, I have no CD of WinXP (OEM installation) - I have a red floppy that points to a NON_DOS partition full of .cabs!

Trouble is said floppy is a Win98 recovery, not WinXP, so I'm worried about that a bit, and I have no DVD-RW (only CD-RW) to backup with, and my HDD is 72.5Gb full. That's going to be lot of lost time if this fails because my recovery disk is duff.

My WinXP isn't dual booting, so Grub won't be touched, WinXP's on another HDD that I smply swap the ATA cable over for when needed. I tolerated the loss of system speed in XP upto now because I'm patient, but shutting on me randomly just down isn't nice...

What I need is a Windows XP CD without the hassle of M$ anti-piracy warnings appearing on my PC, I paid for it afterall, so where's my disk!I don't know if this will help
but if you have access to a XP install CD use it and when you are asked for the install key
use the key on the M$ sticker on your machine (OEM sticker).
Or call the manufacturer for a disc. My sister has a e-machine PC that did not come with a install/restore CD. I called e-machines and even though out of warranty they express shipped a disc for $20.00 USD (basically shipping and handling).

Not sure about the first suggestion but the OEM key on the sticker on your machine
should do the trick. You will still have to activate, either online or by phone.

---

### Post by blore123 on 2007-01-16
So the keys are not linked to CD serial number or anything then (some are, like C&C Generals)?

I really cannot afford to have much downtime on that OS, although now I've got Ubuntu it is not so bad (I do use it for Dreamweaver though :()

---

### Post by Frank Golden on 2007-01-16
> **blore123 said:**
> So the keys are not linked to CD serial number or anything then (some are, like C&C Generals)?

I really cannot afford to have much downtime on that OS, although now I've got Ubuntu it is not so bad (I do use it for Dreamweaver though :()
I don't think so. I think the number on the sticker affixed to your machine is the key.
I built an install disk using instructions found on the net for my sister. The instructions led me to believe that the number from the OEM sticker would work. I did not get to use it however s the disk was bad and wouldn't boot on her machine. We ended up calling the manufacturer and they shipped a disk out in two days.
You can always call M$. for direction. The key on the sticker is what you paid for.

---

### Post by blore123 on 2007-01-16
Seems a lot for some code on a sticker. Anyone want to buy 25 random alphanumeric characters off me for £$?

Thanks anyway...

---

### Post by mikewhatever on 2007-01-16
It may be belated, but still, I do not think deleting files on your Windows partition is the right way to go. Have you considered actually getting help with you spyware? 
[http://www.theeldergeek.com/forum/index.php?showforum=22](http://www.theeldergeek.com/forum/index.php?showforum=22)
You can register and get step by step instructions. I would strongly recommend to stop any activity on the Windows partition before it is messed up to the point of no return.

---

