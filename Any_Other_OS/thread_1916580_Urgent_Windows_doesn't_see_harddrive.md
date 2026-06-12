---
title: "Urgent: Windows doesn't see harddrive"
date: 2012-01-28
forum: Any Other OS
---

### Post by vadboy on 2012-01-28
So I installed linux alongside window 7. 

After installation was finished I couldn't get linux mint wireless to work properly and decided to go back to windows 7, BUT COULDN"T.
The problem started from windows 7 not loading, when I selected to boot to windows, all i got was "windows is starting" window for 2 seconds and then the BLUE SCREEN (which said to prevented a hardware damage, system is restarting).

So next I tried to repair windows, tried to fix bootmanager through bootrec /fixboot. Got frastuated and decided to erase linux mint and reinstall windows 7.
Went to gparted, erased all Linux Mint partitions, and created a new one with NFTS format.

Loaded the windows 7 installer, and when the time came to select the harddrive to install the windows on, the window was empty, saying no harddrives found!

What to do? I am panickinga!

---

### Post by Perfect Storm on 2012-01-28
Moved to Other OS/Distro Talk.

---

### Post by Dlambert on 2012-01-28
I would reformat the entire partition table and see if that works

---

### Post by mips on 2012-01-29
> **Dlambert said:**
> I would reformat the entire partition table and see if that works

Or use dd to zero the drive, takes a bit longer though. Just be CAREFUL to selct the correct drive!!!

---

### Post by varunendra on 2012-01-29
> **vadboy said:**
> Loaded the windows 7 installer, and when the time came to select the harddrive to install the windows on, the window was empty, saying no harddrives found!
Make sure the BIOS detects the drive. If the BIOS can see it, there is no reason why Win7 can't. And if it has disappeared from BIOS as well, or if the BIOS looks like 'struggling' to detect it, then either the drive's cable/connector is loose, or it has just 'gone'!

By the way, the 'BLUE SCREEN' event in Win7 suggests it is a hardware level problem, so looking into BIOS is just a verification, and checking the physical connections maybe a possible fix.

---

### Post by Dlambert on 2012-01-29
> **varunendra said:**
> Make sure the BIOS detects the drive. If the BIOS can see it, there is no reason why Win7 can't. And if it has disappeared from BIOS as well, or if the BIOS looks like 'struggling' to detect it, then either the drive's cable/connector is loose, or it has just 'gone'!

By the way, the 'BLUE SCREEN' event in Win7 suggests it is a hardware level problem, so looking into BIOS is just a verification, and checking the physical connections maybe a possible fix.

+1. I made the mistake of once 35 timing a drive, 4 days later...lol

---

### Post by morbidchimp on 2012-01-29
I mate,

It looks like one of the following things are happening, but I could do with getting a bit more information from you to get the the heart of it. 

Let me ask first;

What is the make model of your computer? (dell/hp/laptop/desktop etc). This will help me identify many possible problems.

How many physical hard drives have you installed in your computer? Commonly people have one drive partitioned in 2 or 3 different sizes. 

When your computer gave you the blue screen of death, it would have given you a STOP error. Do you know what this stop error is?
[http://img694.imageshack.us/img694/5167/shirker.png]("http://img694.imageshack.us/img694/5167/shirker.png") - Can you repost this?

I am assuming the following setup and you more or less went this route to install Mint;

You have one Hard drive in your computer and you chose to Install Linux Mint by booting the CD and choosing to install alongside windows. 

This would have required resizing your existing partitions (which would have contained one or two partitions) to accommodate Linux and at some point between here and finishing install, something went wrong. Linux would have tried to install GRUB and make the required changes to this to add Windows to the boot menu as an option. 

As you said, you didn't get anywhere and in the end opted to Install windows again, likely from either your system recovery partition (usually requiring pressing F11 or similiar on bootup) or from USB/CD.

Assuming your partitions are not messed up and if you had of installed using the restore to factory settings method, you would not have run into the problem you are describing unless your hard disk has died. Is it still visiable from your BIOS? or from Linux Live CD?

So I believe you are installing from ISO/USB/CD etc and it may not be the origional install that came with your computer, you either downloaded it or bought it seperate from your pc or whatever. A common problem on some install's of windows is that they may not contain the drivers required for windows to See your disks at all. When this happens you are usually required to click "HAVE DISK" or similiar during install and provide these drivers for windows to install correctly.

Can you see your disks and partitions from Hirens boot cd, some windows live cd or from a linux boot cd? - If so, this may indeed be the case. If you know the make and model of your computer (hp or whatever) you should be able to download the drivers you need from the manufactures website. 

If you built the pc yourself or if its some other not so common make, or your own custom motherboard in there you will need to find the manufacture of the motherboard most likely and identify what motherboard you have and download the drivers from there. 

What I think is that the install you are using to re-install Windows 7 does not contain the Disk drivers for your disk controller. Linux can obviously see the disks, and Windows prior to all was working grand because it had the required drivers already installed. 

90% of the time windows will see your disks, but sometimes it can't if it doesn't have the drivers. Usually you are given an oppertunity to do so.


Failing all that, if you can't see your disks from a Linux Live CD, or some other boot cd - your disks may be screwed. 

What is your current partition setup?

If you can post your actual setup, what you've done, and relevent hardware details I'll try and help a bit more. 

Best regards,





EDIT: ps - the fact you were getting the blue screen of death does can be either a software or a hardware problem. If somehow Mint screwed partitions up, or data was lost or corrupted somehow, a blue screen can happen and indicate a hardware problem when its not actually that at all. If you post the stop error it will be a strong indication of where the problem lies. Given a few checks on some things after we know what error it is you will be easily able to figure out if you have a hardware problem, or software problem after that by running additional tests.

If you were having problems before you installed mint, or you installed mint because of problems and you wanted to try something else - its likely you may have a hardware problem. The installation process is pretty good and its rare in the grand scheme of things people experience problems unless there is something out of whack.

---

