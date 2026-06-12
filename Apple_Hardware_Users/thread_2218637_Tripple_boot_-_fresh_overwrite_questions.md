---
title: "Tripple boot - fresh overwrite questions"
date: 2014-04-21
forum: Apple Hardware Users
---

### Post by Rahabib on 2014-04-21
I have a triple boot Macbook Pro 5,2 that I have been updating since 9.04.  The last two versions (13.04, 13.10) seem to have a lot of config issues and bugs likely due to limping along legacy configs etc. (not completely sure).  As a result, I thought I would try to wipe 13.10 and start fresh with 14.04.  I have reFit on it, and just wanted to know if there is a trick to wiping just 13.10 keeping my Win7 and OSX10.9 intact.

I would assume during install, I choose "other" then wipe out just the ext4 volumes and set up my swap and root dir in the new unallocated space.  I guess I would just keep grub at default since there is only one drive available.  Correct me if I am wrong with this portion.

From there, I am unsure what I need to do for reFit.  Do I need to boot into OSX and install reFit again to fix it?  How do I do this if reFit is gone? Can I still hold the "option/alt" key to get into OSX and windows if reFit/boot EFI is changed/damaged?

Thanks for any help!

---

### Post by Tutoned on 2014-04-21
This works on my MacBook Pro: [https://www.youtube.com/watch?v=O40UG1guLeo](https://www.youtube.com/watch?v=O40UG1guLeo)

---

### Post by Tom 6 on 2014-04-21
Hi :)
I haven't got a complete answer but can answer some of the issues.  

You don't need to delete any partitions.  Just install over the top of whatever is in the existing Ubuntu partition.  

Yes, use the "other" option at the bottom of the partitioning section.  Over the years it's been renamed from "Something else", "Advanced", "Manual" but it's always at the bottom of that partitioning screen.  I think about screen 4-6(ish), maybe even earlier.  Note that the back button does work for quite a long way through the installer.  

The "Other" option should get you to a vertical list of all the partitions on your hard-drive.  You can click on the relevant one (errr, i tend to open GParted so that it's easier for me to work out which is the correct partition(s)) and then click on the "Change" button under the list.  Choose "Use partition", if you set it to the same file-system as the existing partition then it even allows you to NOT reformat the partition and that might keep your files intact.  All your configs will be over-written though.  Well, all the important ones.  The swap will get reformatted automatically but that doesn't contain any useful data anyway (well, shouldn't do).  

Yes, keep grub at the default.  That should be the hard-drive.  Err so if you have partitions such as sda1, sda2 etc then grub goes to sda  (note no number at the end).  Grub is the "GRand Unified Boot-loader" and that should automatically create a boot-menu for you and it should automatically find all the other OSes for you, even if you had trouble booting into them.  

Regards from Tom :)

---

### Post by Rahabib on 2014-04-22
> **Tom 6 said:**
> Hi :)
I haven't got a complete answer but can answer some of the issues.  

You don't need to delete any partitions.  Just install over the top of whatever is in the existing Ubuntu partition.  

Yes, use the "other" option at the bottom of the partitioning section.  Over the years it's been renamed from "Something else", "Advanced", "Manual" but it's always at the bottom of that partitioning screen.  I think about screen 4-6(ish), maybe even earlier.  Note that the back button does work for quite a long way through the installer.  

The "Other" option should get you to a vertical list of all the partitions on your hard-drive.  You can click on the relevant one (errr, i tend to open GParted so that it's easier for me to work out which is the correct partition(s)) and then click on the "Change" button under the list.  Choose "Use partition", if you set it to the same file-system as the existing partition then it even allows you to NOT reformat the partition and that might keep your files intact.  All your configs will be over-written though.  Well, all the important ones.  The swap will get reformatted automatically but that doesn't contain any useful data anyway (well, shouldn't do).  

Yes, keep grub at the default.  That should be the hard-drive.  Err so if you have partitions such as sda1, sda2 etc then grub goes to sda  (note no number at the end).  Grub is the "GRand Unified Boot-loader" and that should automatically create a boot-menu for you and it should automatically find all the other OSes for you, even if you had trouble booting into them.  

Regards from Tom :)

Thank you, this was quite helpful.  I still would like some assurance that I can boot into all of the OSes.  I have had MBR issues with Windows and had to use a live CD to get it back, adding reFIT into the mix, I havent seen any information about recovering that.

---

### Post by Tom 6 on 2014-04-22
Hi :)  
This thread might be helpful.  
[http://ubuntuforums.org/showthread.php?t=2218456](http://ubuntuforums.org/showthread.php?t=2218456)

Wrt the MBR issue with Windows it quite complicated to explain but easy to deal with ...   

Each time you install a boot-loader it loads a part of itself into the MBR.  Each drive has only 1 MBR and the contents points to which boot-loader to use.  When you install Windows it installs it's own boot-loader without asking and it's boot-loader is blind to all other systems.  

So, the best bet is to install Ubuntu last.  It uses the "Grub2" boot-loader which usually finds all other OSes and set-up a boot-menu to include them all.  

If you really have to install Windows after anything else and already have Ubuntu on the system, then you only need to reinstall the Grub boot-loader.  The best way to do that is to boot a "LiveCd", or even better a "LiveUsb" session (usbs are about a thousand times faster than a Cd aren't they?) and then search for the "Community Documentation" page on Grub2.    Actually therer are many good articles on how to reinstall grub2 but there is also a LOT of FUD out there about it, deliberately making something really easy into a nightmare.  

Regards from 
Tom :)

---

### Post by Rahabib on 2014-04-22
Thanks. Windows and OSX are already installed. I am just wiping out Ubuntu for a fresh install to hopefully help with some of the crashing and errors I have been getting lately.  I may just update to 14.04 via update manager and see if those updates fix some of the issues I have been having.  If not, I guess Ill need a clean Ubuntu install.

I wonder if I can install rEFInd from Ubuntu?  If so, I guess I can always use a LiveUSB session and install that way.

---

### Post by Tom 6 on 2014-04-22
Hi :)  
I never bother wiping Ubuntu.  Just do a fresh install over the top.  I tend to avoid reformatting the Ubuntu partition(s) too.  The swap get reformatted anyway but avoiding reformatting the / and more especially the /home (probably inside the /) has some interesting effects.  

From the looks of it you don't have to worry about the rEFInd at all but i didn't read the thread too closely so i could easily be wrong.  
Regards from 
Tom :)

---

