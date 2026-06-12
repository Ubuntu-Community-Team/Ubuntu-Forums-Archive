---
title: "Dual boot problems - giving up for now - 10 hours after start - 6 hours of threads"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by mitch_scaff on 2007-09-09
It' s been about 10 hours since I started the installation of Ubuntu.  Ubuntu installed OK, but I couldn't get Vista to run again.  After I got an internet connection using a different machine, I logged into the forums and found out that others have had similar problems.  But I did not find a solution.  There's stuff about mounting.  There's stuff about finding what's bootable.  There's stuff about MRB and grub.  And the more I read, the more I find terms and commands and files whose purpose and context I don't know anything about. 

so I'm going to reinstall Vista, and worry about trying again in a few days or a few weeks.  I hate the fact that I'm going to wipe away my accomplishments (such as they were) in the process. I also don't like "giving in" to the inferior operating system Microsoft has produced, and giving into the near monopolistic corporation that they are. 

I need to do this, but my expectations have shifted.  I thought I could follow the directions in the book (Ubuntu Linux for Dummies) and be done in a couple of hours.  I find out I have an older version (6.10).  And I spent 10 hours  - some of which I could ill afford.  Instead of being jazzed, I'm now frustrated and dreading my next attempt.  ](*,)

At least I'll know to drop back here again before I start again. 

  Thanks again to those who offered help. O:)

---

### Post by maniac_X on 2007-09-09
Don't give up. Rome wasn't built in a day :) I know your feeling of frustration. I've done many wipes/reinstalls myself because I fubared a install and couldn't always make sense of info in the forums. You'll notice my avatar...I chose it because that's how I feel sometimes when playing around with Ubuntu. Just step back, let the frustration go and come back to it in a few days. One step at a time.

Good luck and hang in there.

---

### Post by eph1973 on 2007-09-09
Here are some options you might want to try:

Option #1:
I don't know if you have already gone to this web site, but try checking out: [http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)
However, this website uses Feisty Fawn, version 7.04 of Ubuntu to show you how to set up your dual boot scenario, so if you didn't download that image, you would have to download and burn the image for Feisty.

Option #2:
Use Wubi to run Ubuntu.  Some information about Wubi, and how it works is at this web site: [http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

Option #3:
You could try Knoppix available from here: [http://www.knoppix.net/](http://www.knoppix.net/)
Knoppix is a flavor of Debian Linux run from a CD.  That website has a wiki that hopefully will answer most of your questions about it.  

I don't know if any of these three options are what you are looking for, but unless you have already read about it and tried it before, most likely option #1 should work pretty well for you.  If not, the other two options give you ways of installing Linux without dealing with partitions and all that, yet give you an opportunity to learn how to use Linux so that hopefully one day you will return to option #1.

Hope this helps :-)

---

### Post by dwhitney67 on 2007-09-09
I have read many posts in the Ubuntu forum about the headaches associated with setting up dual-boot systems.

Do you require a dual-boot system?  It seems that you are not fond of MS.  In such case, merely ensure that you CD-ROM drive is the first to be searched during boot up, and then install the latest version of Ubuntu (7.04) or one of the other distros of Linux.

If your system has an ATI video chip-set, then I recommend booting from the Ubunut "alternate" CD, which is a different beast than the regular Ubuntu CD.

In any case, you must understand that an old distro (6.x of Ubuntu) probably does not have included with it the device drivers necessary to operator a new-generation system.  One could argue the same with Win-2000.

Get yourself the latest version of Ubuntu and then try again.

---

### Post by logos34 on 2007-09-09
You don't need to reinstall vista.  Just restore the bootloader.  

Boot from the Vista install DVD and look in the 'boot' folder for a program called bootsect.exe.  Run

> bootsect.exe /nt60 C: 

[http://technet2.microsoft.com/WindowsVista/en/library/49ded4da-b66f-4b42-9563-04c218a1a6ac1033.mspx?mfr=true](http://technet2.microsoft.com/WindowsVista/en/library/49ded4da-b66f-4b42-9563-04c218a1a6ac1033.mspx?mfr=true)

[http://support.microsoft.com/default.aspx/kb/927392](http://support.microsoft.com/default.aspx/kb/927392)

OR 

use [VistaBootPro]("http://www.vistabootpro.org/") to restore vista bootloader.

To boot ubuntu get [Super Grub CD]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html").

And/or add a boot entry for Edgy 6.10 to the vista bootloader using [EasyBCD]("http://neosmart.net/wiki/display/EBCD/Linux").

Now you can boot linux either from SuperGrub CD or using Vista.

Consider a fresh install of Gutsy 7.10 when it's released (due out next month). If you want to continue using vista bootloader, then you want to put Grub on the root partition instead of the MBR.  Or let Grub overwrite the vista loader and maybe it will work this time.

---

### Post by Computer Guru on 2007-09-09
> **logos34 said:**
> You don't need to reinstall vista.  Just restore the bootloader.  

Boot from the Vista install DVD and look in the 'boot' folder for a program called bootsect.exe.  Run



[http://technet2.microsoft.com/WindowsVista/en/library/49ded4da-b66f-4b42-9563-04c218a1a6ac1033.mspx?mfr=true](http://technet2.microsoft.com/WindowsVista/en/library/49ded4da-b66f-4b42-9563-04c218a1a6ac1033.mspx?mfr=true)

[http://support.microsoft.com/default.aspx/kb/927392](http://support.microsoft.com/default.aspx/kb/927392)

OR 

use [VistaBootPro]("http://www.vistabootpro.org/") to restore vista bootloader.

To boot ubuntu get [Super Grub CD]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html").

And/or add a boot entry for Edgy 6.10 to the vista bootloader using [EasyBCD]("http://neosmart.net/wiki/display/EBCD/Linux").

Now you can boot linux either from SuperGrub CD or using Vista.

Consider a fresh install of Gutsy 7.10 when it's released (due out next month). If you want to continue using vista bootloader, then you want to put Grub on the root partition instead of the MBR.  Or let Grub overwrite the vista loader and maybe it will work this time.

Actually, you can do all three of those steps with EasyBCD. 
Once your in Vista from GRUB, you can use EasyBCD's Bootloader Managment page to reinstall the Vista bootloader. Then you can use either NeoGrub or Grubless Linux to boot into Ubuntu *without* installing GRUB to the bootsector.

---

### Post by logos34 on 2007-09-09
> **Computer Guru said:**
> Actually, you can do all three of those steps with EasyBCD. 
Once your in Vista from GRUB, you can use EasyBCD's Bootloader Managment page to reinstall the Vista bootloader. Then you can use either NeoGrub or Grubless Linux to boot into Ubuntu *without* installing GRUB to the bootsector.

Yes, but the problem is that the OP can't get grub to boot vista.  So he'll have to restore the bootloader from the vista dvd repair environment in order to get into vista.  *Then* he can run the easybcd .exe installer which will allow him to edit vista loader to boot ubuntu by either chainloading grub (in which case it has to be on the bootsector of the root partition) or directly the way you mentioned using the Neogrub option.

My point was basically to provide options. Super Grub is something he definitely wants to have on hand if he dual boots.  But maybe he doesn't want to use easybcd and edit the bootloader and all that jazz.  Dunno.  Sounds to me like he needs a rest...I sympathize because I remember my first install of linux and it wasn't pretty!

---

### Post by mitch_scaff on 2007-09-10
OK we're now on day 3 of our quest for a Vista / Ubuntu dual boot machine. 

When we left it last night, we were still booting Ubuntu fine, but trying to boot Vista resulted in the black screen of frustration.  (Usually after getting 45 seconds or more of funny green progress indicator, saying that Microsoft Windows was trying to load)  

If I interrupt the normal boot process (hitting f8 after the gateway logo appears), I can direct the machine to boot off a CD.  

If I put the Window's Vista CD in, it will load a bunch of files, then 
give me the green progress indicator for a while, then revert to the black screen of frustration.  There does not appear to be a recovery mode option.

If I let it boot using its defaults, it will load grub, which will give me three ubuntu options and two vista options.  The main default ubuntu option works fine.  The vista options give me progress indicator followec by black screen of frustration.

Is it possible that my version of Ubuntu (6.10 shipped with the Ubuntu for dummies book) is looking not for bootmgr but for ntldr?

---

### Post by mitch_scaff on 2007-09-10
I should have said, "my version of grub, that comes with Ubuntu 6.10"

---

