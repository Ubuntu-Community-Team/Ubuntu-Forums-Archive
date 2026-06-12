---
title: "Cleaning up."
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by miguelangelo1986 on 2007-06-25
I wanna give Ubuntu more space. I'd like to know what do I do to make a complete cleaning up in my Windows XP, I mean send all to the trash and maintain only the things that make the Internet run. It's kind of a formatting. How can I do such a thing?

---

### Post by davecambs on 2007-06-25
you should go to add/remove programs via the control panel and remove any installed programs that are not needed, then you can run diskcleanup (Start | Programs | Accessories | System Tools | Disk Cleanup) to get rid of any unnecessary files that are cluttering up your XP install.

As always be careful in what you do and only remove things you are 100% sure about.

---

### Post by r4ik on 2007-06-25
Any reason not to go linux all the way ?

---

### Post by BobCFC on 2007-06-25
First step I would use Add/Remove programs in Control Panel.  This should give an estimate of size so you can remove big programs that you don't need any more.

Then I would clear out you Browser Cache.  In IE6 Tools->Internet Options then under Temporary Internet Files choose delete all.   IE7 is similar.   In firefox  choose Tools->Clear Private Data and make sure Cache is ticked.

Then I would hunt for temp files.  These are files used while unzipping or installing that you don't need any more.  Look in Documents and Settings->(Username)->Local Settings->Temp.   

There is also a temp folder in Windows->Temp.  You can delete anything in these folder.

Speaking of user you can remove any extra User Accounts that you don't need from Control Panel->Users.   This will delete all their settings and Doc folders.

Here is quote from Microsoft dot com about how to turn off System Restore...  SR basically keeps extra copies of your files lying around as backups

> Method 2: Manual steps to turn off or turn on System Restore
Steps to turn off System Restore
1.	Click Start, right-click My Computer, and then click Properties.
2.	In the System Properties dialog box, click the System Restore tab.
3.	Click to select the Turn off System Restore check box. Or, click to select the Turn off System Restore on all drives check box.
4.	Click OK.
5.	When you receive the following message, click Yes to confirm that you want to turn off System Restore:
You have chosen to turn off System Restore. If you continue, all existing restore points will be deleted, and you will not be able to track or undo changes to your computer.

Do you want to turn off System Restore?
After a few moments, the System Properties dialog box closes.

Now you can look in System Volume Information for copies of files.  I found gigs in there and didn't break anything by deleting files but you might want to research this further if you are worried.

You might have a big hibernate file on your C: drive next to your pagefile.  To turn off hibernation right-click on Desktop choose properties to get Display Options..  On Screensaver tab click Power.... On Hibernate Tab uncheck Hibernate..  May need to reboot I don't know..  But this will remove a file the size of you memory.. So if you have 1gb it will free another gig from C: drive.

Finally you could do a file search and in advanced search for files over 50 or 100mb.  See whats lying around.. some old movie or something.   It's in bytes so 1024x1024xMEG ...50mb =  52428800     100mb = 104857600


Just off the top of my head, good luck

EDIT:  You might need to turn on hidden and system files in View->Folder Options or something
EDIT2: oh yeah Empty Recyle Bin afterwards of course lol

---

### Post by miguelangelo1986 on 2007-06-25
Thanks a lot, buddy. I'll give it a shot.

---

### Post by DrRootabega on 2007-07-14
You might also try Ccleaner.  It removes all the unneeded temporary files and other useless stuff that windows puts on your harddrive.  I encourage you to go through ALL the options and make sure that it doesn't delete anything that you want-it can be quite aggressive.

you can get it here:
[http://www.download.com/3000-2144_4-10315544.html](http://www.download.com/3000-2144_4-10315544.html)

---

