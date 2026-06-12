---
title: "formatting"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by pardesi on 2007-09-08
my friend wants to format his computer .he dual boots XP ubuntu fiesty.what steps should he atke to be on the safer side.he is a noob(so am i)and just wants to have windows after formatting

please help.

---

### Post by expatCM on 2007-09-08
If all he wants is Windows and if the present data on the drive is all backed up then simply boot the system from the Windows CD and follow the instructions on screen.....

---

### Post by Xorg.conF on 2007-09-08
Well first I have to say that I hope your experience with Ubuntu was a good one and later realize your mistake of switching to Windows. 
	I don't know your level of experience with computers, I will try to be as accurate as possible in the steps to take.  
	 If I am understanding correctly you want to format your hard drive and install the windows operating system, to do this, first you must take the obvious action of backing up your data and documents before you begin because everything will be erased afterwards.  You can do this by either burning them onto discs or UsB storage devises etc...  Just do it.  
	These are just general instructions that might seem a little inexplicit
, I wont go in-depth because there's simply too many things to state.  All you have to do to begin is to pop the Windows XP  Disc into your cd rom drive, and restart the computer with the disc still inside.  Now here's where I might have a problem in helping you, normally it will say press any key to continue, if it says that, great then do it.  If not, your BIOS might not have the proper boot order, witch means that it might not run from the cd, just boot from your hd when your computer is turned on.  In this case there has to be a key to press that gives you boot options, such as the F12 key in Dell BIOSes, it will come up when starting of the computer. 
	After choosing boot from cd rom in boot options, you will have to wait as the Windows disc loads and caches drivers and modules essential for the instillation process, just looks like a big blue screen with words flashing at the bottom. 
	You will have to follow a set of questions by pressing the keys stated at the bottom of the blue screen to continue, such in the beginning when it tells you to press F8 if you agree with the licence terms.  Do this up until you come to a screen displaying your current hard drive configuration, stating all the partitions and what file systems each are formatted in, with a drive letter such as, C: for Windows XP, they will all be in a rectangular box, easy to distinguish.  what you have to do, if you really want windows only, is to delete all partitions except your recovery partition, if you need it.  You can do this by using the proper keys assigned at the bottom, there's one for deleting, create partition, etc... .  After deleting them all, you will be left with a line in the box that says unpartitioned space #### whatever the amount of space your hd is, that along with your recovery partition, if you have one or won't because you chose to delete it.  
	Create a partition in the unpartitioned space using the whole amount of space, then it should read partition 1 new_raw, or 2, depending on the circumstances.  After that you install on that partition with choosing NTFS (quick) when prompted for choosing a file system.
	the rest should be easy, it will format the hd, then copy the contents of the cd on the hd, then it will restart the computer, do NOT boot back into the cd.  the instillation will continue with about five steps, one of them being dynamic upgrade.  It will ask you general questions during the instillation such as time zone and country, you should be able to handle it yourself.		
	the rest is easy do it yourself.	
	 
    If there's any more problems, tell me exactly what it is, I can help you but I need to know a lot about your computer.  Also so I wont have to explain a lot next time

---

### Post by pardesi on 2007-09-08
thanks 
**@Xorg.conf** it is my friend who is formatting
thanks i will handover him this

---

