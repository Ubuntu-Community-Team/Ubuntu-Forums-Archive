---
title: "Win XP Recovery Console substitute"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by blastthisinferno on 2007-08-08
I tried looking for a substitute to the Win XP cd recovery console but with no luck I came here.  My problem is that I had a hard drive that was a dual boot of Win XP home and Gentoo.  I foolishly deleted the Gentoo partition because I never use it (I was just messing around with it for a while).  The Gentoo partition had the Grub on it that allowed me to choose between Windows and Gentoo.

So now that I don't have Grub, I can't boot to Windows.  So I tried the Windows Recovery Console, which would probably work fine, but when I get to this part
```
1: C:\WINDOWS

Which Windows installation would you like to log onto
(To cancel, press ENTER)?  1
Type the Administrator password:
```

I type my password and I get 
```
The password is not valid.  Please retype the password.
Type the Adminstrator password:
```

Is there a way to install Grub on the Windows partition with a live cd?  Is there a way to get around this password if I can't get into Windows?

---

### Post by Rocket2DMn on 2007-08-08
If you get to the Windows recovery console and type "fixmbr" you should be set to go.  There probably isn't an administrator password, try leaving it blank (or use your Windows password if you have one)

---

### Post by cobrn1 on 2007-08-08
You could download the super GRUB Disc and see if that can fix this for you...

Do you not remember the admin password tho - you'll have selected one when you first installed windows (I'm assuming it's Pro edition).

---

### Post by oilchangeguy on 2007-08-08
when prompted for the admin. password, just press enter.
and read this:
Using the Recovery Console to Replace the MBR

You can use the fixmbr command in Recovery Console to rewrite the MBR to resolve a corrupted MBR on a startup disk. However, running fixmbr overwrites only the master boot code, leaving the existing partition table intact. If the corruption in the MBR affects the partition table, running fixmbr might not resolve the problem.

Caution Use this command with care because it can damage your partition table if any of the following apply:
•	

A virus is present and a third-party operating system is installed on the same computer.
•	

A nonstandard MBR is installed by a third-party disk utility.
•	

A hardware problem exists.

Caution Run antivirus software before you use the fixmbr command.
To start the computer and use the Recovery Console to replace the MBR

1.
	

Insert the Windows XP Professional Setup CD-ROM into the CD-ROM drive.

2.
	

Restart the computer. If prompted to press a key to start the computer from the CD-ROM, press the appropriate key.

3.
	

When the text-based part of Setup begins, follow the prompts. Press the R key to repair a Windows XP Professional installation.

4.
	

If you are repairing a system that has more than one operating system installed, from the Recovery Console choose the Windows XP Professional installation that you need to repair.

Note If you press ENTER without typing a number, the Recovery Console quits and restarts the computer.

The Recovery Console might also show valid installations of Windows NT 4.0. However, the results of attempting to access a Windows NT 4.0 installation can be unpredictable.

5.
	

When prompted, type the Administrator password. If you do not have the correct password, or if the security database for the installation of Windows XP Professional you are attempting to access is corrupted, Recovery Console does not allow access to the local disks and you cannot repair the MBR.

6.
	

To replace the MBR, at the Recovery Console command prompt, type:

fixmbr

7.
	

Verify whether you want to proceed. Depending upon the location and the cause of the corruption within the damaged MBR, this operation can cause the data on the hard disk to become inaccessible. Press the Y key to proceed, or press the N key to cancel

---

### Post by blastthisinferno on 2007-08-08
I know my password for when I log on.  My account is set as the administrator I believe.  It isn't recognizing that it is my password.

I am using a Win XP Pro cd for the recovery console even though I have Win XP Home on the partition.  I can't find my Win XP Home cd, even if that matters.

Edit:  I have tried just pressing ENTER and it gives me the same password is not valid crap.

---

### Post by oilchangeguy on 2007-08-08
> **blastthisinferno said:**
> I know my password for when I log on.  My account is set as the administrator I believe.  It isn't recognizing that it is my password.

I am using a Win XP Pro cd for the recovery console even though I have Win XP Home on the partition.  I can't find my Win XP Home cd, even if that matters.

as i said, when prompted for the password, don't type anything. just press enter.

---

### Post by cobrn1 on 2007-08-08
Did you install windows yourself. If you did then you may have been asked for an admin password when setting up (yes, there is a super-special admin account even on windows pcs, it's just that normal users have almost exactly the same rights as it...).

If you can remember that then type that in - it is not looking for you normal account's password, the admin account pasword is distinct... If just pressing enter isn't working for you then you may not be able to use it.

However you could just use the super GRUB disc to reinstall GRUB to the MBR. See link in my sig.

---

### Post by cobrn1 on 2007-08-08
WOW - I got my 100th bean without even realising it... :D

Anyway, I had a look and if you want to reset your admin password you may want to have a look at this link: 

[http://pubs.logicalexpressions.com/pub0009/LPMArticle.asp?ID=305](http://pubs.logicalexpressions.com/pub0009/LPMArticle.asp?ID=305)

BTW, I still recommend you have a look into the Super GRUB Disc.

EDIT: infact, if you just google 'windows reset administrator password' you'll find alot of thing which might be of help to you.

---

### Post by psusi on 2007-08-08
Wow, the recovery console should not be asking for a password if you boot from the cd.  

As an alternative, dig up an old dos or 9x boot floppy and use fdisk /mbr to fix it.

---

### Post by oilchangeguy on 2007-08-08
> **psusi said:**
> Wow, the recovery console should not be asking for a password if you boot from the cd.  

As an alternative, dig up an old dos or 9x boot floppy and use fdisk /mbr to fix it.

has it been awhile since you've seen the windows recovery console?
got this info from microsoft's website: see #4

How to use the Recovery Console
You can enable and disable services, format drives, read and write data on a local drive (including drives that are formatted to use the NTFS file system), and perform many other administrative tasks. The Recovery Console is particularly useful if you have to repair your computer by copying a file from a disk or CD-ROM to your hard disk, or if you have to reconfigure a service that is preventing your computer from starting correctly.

If you cannot start your computer, you can run the Recovery Console from the Microsoft Windows XP startup disks or the Windows XP CD-ROM. This article describes how to perform this task.

After Windows XP is installed on your computer, to start the computer and use the Recovery Console you require the Windows XP startup disks or the Windows XP CD-ROM.

For more information about how to create Startup disks for Windows XP (they are not included with Windows XP), click the following article number to view the article in the Microsoft Knowledge Base:
310994 ([http://support.microsoft.com/kb/310994/](http://support.microsoft.com/kb/310994/)) Obtaining Windows XP Setup boot disks
Note To start the computer from the Windows XP CD-ROM, you must configure the basic input/output system (BIOS) of the computer to start from your CD-ROM drive.

To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.	Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.	When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.	If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.	[COLOR="black"][COLOR="Yellow"]When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.[/COLOR][/COLOR]
5.	At the command prompt, type the appropriate commands to diagnose and repair your Windows XP installation.

For a list of commands that are available in Recovery Console, type recovery console commands or help at the command prompt, and then press ENTER.

For information about a specific command, type help commandname at the command prompt, and then press ENTER.
6.	To exit the Recovery Console and restart the computer, type exit at the command prompt, and then press ENTER.

---

### Post by oilchangeguy on 2007-08-08
just found a registry edit that will stop the prompt for a password in the recovery console:



On many XP installations you can't start the Recovery Console because it won't recognize your password. This registry edit causes the Recovery Console not to ask for a password. This works for both XP Home and XP Professional.

Start | Run | Regedit
Navigate to HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WindowsNT\CurrentVersion\Setup\RecoveryConsole
Set the DWORD SecurityLevel value to 1
Exit Registry and Reboot

---

### Post by Paulmd on 2007-08-09
> **blastthisinferno said:**
> I tried looking for a substitute to the Win XP cd recovery console but with no luck I came here.  My problem is that I had a hard drive that was a dual boot of Win XP home and Gentoo.  I foolishly deleted the Gentoo partition because I never use it (I was just messing around with it for a while).  The Gentoo partition had the Grub on it that allowed me to choose between Windows and Gentoo.

So now that I don't have Grub, I can't boot to Windows.  So I tried the Windows Recovery Console, which would probably work fine, but when I get to this part
```
1: C:\WINDOWS

Which Windows installation would you like to log onto
(To cancel, press ENTER)?  1
Type the Administrator password:
```

I type my password and I get 
```
The password is not valid.  Please retype the password.
Type the Adminstrator password:
```

Is there a way to install Grub on the Windows partition with a live cd?  Is there a way to get around this password if I can't get into Windows?


Note that the Administrator password and the user password are not necessarily the same. In many cases the Administrator password is blank. This is especially the case in a user installed XP. So try leaving the password blank when it asks for one.

If that fails: There is still a way around this: boot in to the recovery console with a Windows 2000 CD (not a typo!) .  You will be able to completely bypass that password glitch (it's a long standing security hole that's never been patched). All the recovery console functionality will work.

---

### Post by Paulmd on 2007-08-09
> **blastthisinferno said:**
> I know my password for when I log on.  My account is set as the administrator I believe.  It isn't recognizing that it is my password.

I am using a Win XP Pro cd for the recovery console even though I have Win XP Home on the partition.  I can't find my Win XP Home cd, even if that matters.


Edit:  I have tried just pressing ENTER and it gives me the same password is not valid crap.

It often does matter. Likely it will work if you can find an XP home CD (or a win2kcd). I've come across this issue before. Wrong version of XP cd means it doesn't recognize the password, but the friggin win2k CD does work. Go figure.

---

