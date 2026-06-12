---
title: "[SOLVED] Partition during installation"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by machavillain on 2007-07-18
Basic question: When I selected "Guide partition" (with a sub-bullet that reads "Entire disk"), does this mean it will set up a dual boot, or just wipe my hard disk and install Ubuntu-only boot?

Would post a screenshot, but I'm at work...

---

### Post by machavillain on 2007-07-18
I should add that the screens at [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall) are not exactly what I am seeing...

---

### Post by wolfen69 on 2007-07-18
yes, it will wipe the drive and install ubuntu on whole drive.

---

### Post by wolfen69 on 2007-07-18
i believe the screenshots you linked to are for version 6.06. it has changed a little in 7.04.

---

### Post by machavillain on 2007-07-18
Thanks for the quick reply. Next problem: as far as I can tell, when I select "manual", it doesn't actually let me adjust the size of the partitions. Screenshot: [http://www.flickr.com/photos/padraics_travels/841239443/](http://www.flickr.com/photos/padraics_travels/841239443/)

---

### Post by Kheldin on 2007-07-18
That's because they've already been setup, probably from Windows.

Looking at your screenshot, it appears you have no free disk space to create any partitions either. I guess knowing whether or not you want to dual boot is the main question here. If not, just blow that all away and let Ubuntu install. If you need a dual boot you should have left some free space when you installed windows for Ubuntu to install on. I could be wrong on this.. and you may be able to adjust your NTFS partitions (although I don't recommend it even if you could).

Also if you want to dual boot, and you have never ventured down this path before, I suggest you read a little bit about grub as well as search the forums here for 'dual boot' as there are many great links to guides to help you understand it and set it up successfully.

---

### Post by machavillain on 2007-07-18
I've had Windows installed since before I even thought about Ubuntu, but have never tried to set up a partition. My laptop is an HP, which came pre-loaded with a partition from which to burn the "HP Recovery" DVDs. After doing so I eliminated the "drive". Is that what this is about?

I do want to dual boot, just because I'm nervous, but if it's just too complicated, I may take the plunge. How steep of a learning curve am I looking at if I just jump in?

---

### Post by jcronkhite on 2007-07-18
I did the same thing with a dual boot.  Basically, it was all automatic for me.  I too have an HP with the recovery partition you mentioned.  What I did was this:

[LIST=1]
[*]I made my recovery DVD's for the HP
[*]Once I was sure they were good, I used the HP Recovery Utility Software to remove the recovery partition and recover the space it was wasting
[*]I resized the partition so I could install Ubuntu Feisty on 50% of the drive.  I used GParted, a live and free boot CD to perform the resize.  Now Windows Vista is taking up only half of the drive at this point, and half of the drive is unpartitioned space.
[*]Next I installed Ubuntu Feisty selecting the empty partition during setup (I think that's what I did, it's been a while)
[*]Finally, I rebooted the system and was presented with the GRUB menu, which automatically added Windows Vista as a menu item.
[/LIST]

Long story short, Ubuntu boots up just fine, if I choose to run Windows Vista (which I do for my iPod and HDTV needs) I have the option at startup.  The menu setup was done automatically and Windows was left intact and bootable.

---

### Post by machavillain on 2007-07-18
Wow, that's all very reassuring. I've run the Recovery Utility and eliminated the drive/partition - is that small partition that's left just a residual? Not that it matters, I suppose. So I just need to resize that small partition to a reasonable size for Ubuntu, like 20GB?

---

### Post by jcronkhite on 2007-07-18
That's what I would do.  Basically, You want your Windows partition resized but intact and bootable.  Then you want the remaining space on the entire drive dedicated to Ubuntu (unless you have other plans).  Mine is 60GB NTFS as the first Windows partition, and 60GB empty space used for the Ubuntu install.  I think 20GB should be fine for Ubuntu.  I also have a second hard drive that is a FAT32 120GB 100% usage partition that I share between Windows and Ubuntu.  I make this point to give you something to consider in the event you want a shared volume as well.  Hope this helps!

---

### Post by machavillain on 2007-07-18
Well, I've backed up all my important stuff...so here goes.

---

### Post by jcronkhite on 2007-07-18
Good luck!  Let us know how it goes :)

---

### Post by machavillain on 2007-07-18
So, when I tried to enlarge the smaller partition, I can't: [http://www.flickr.com/photos/padraics_travels/847748710/](http://www.flickr.com/photos/padraics_travels/847748710/)
And when I tried to shrink my large partition (which I think would actually leave me with 3 partitions, I get an error): [http://www.flickr.com/photos/padraics_travels/847748706/in/photostream/](http://www.flickr.com/photos/padraics_travels/847748706/in/photostream/)

Thanks for all the help so far - any ideas now?

---

### Post by jcronkhite on 2007-07-18
What does the error message say when you expand it (screenshot 2, click the arrow, it will expose another arrow a few more times until you see the final error message).  I've had problems resizing Windows partitions when Windows wasn't shutdown properly.  Usually booting normally and running a scandisk in Windows resolves this for me.

---

### Post by machavillain on 2007-07-18
[http://www.flickr.com/photos/padraics_travels/847748706/in/photostream/](http://www.flickr.com/photos/padraics_travels/847748706/in/photostream/)

Looks like you were right - is chkdsk the same as Scandisk?

---

### Post by jcronkhite on 2007-07-18
Sorry, yeah it is.  I always mix up the old DOS scan vs. the windows equivalent.  The main thing is to be sure your Windows partitions are in good "health".  Run the scans and perform a proper shutdown before resizing and you should be okay.

---

### Post by machavillain on 2007-07-18
So, I got much further along in the process this time, but ultimately still ended up with an error message [[http://www.flickr.com/photos/padraics_travels/847081659/]](http://www.flickr.com/photos/padraics_travels/847081659/]). However, the new, empty partition is now showing up [[http://www.flickr.com/photos/padraics_travels/847081669/]](http://www.flickr.com/photos/padraics_travels/847081669/]). Is there something I need to do to reconcile those errors, or should I just go ahead with the "most free space" guided installation? Thanks again.

---

### Post by machavillain on 2007-07-18
I have now have these options in the install: [img]http://farm2.static.flickr.com/1010/848272018_33c282998d_o.png[/img]. Can anybody tell me which one of these I want, if I want to set a dual boot (and put Ubuntu on that unallocated partition)?

Hopefully this will be my last question and then I can leave you all alone...

---

### Post by bigboy_pdb on 2007-07-19
I'm pretty certain that you should use "Guided - use the largest continuous free space", but since other people are helping you you might want to wait for someone else to verify this.

EDIT: You could use "Manual" but I don't recommend doing this if you don't know what mount points you need to create and how big the partitions should be for each section of the hard drive that corresponds to the mount point.

---

### Post by machavillain on 2007-07-19
Yeah, I used the guided option and everything seems to be working fine. Both XP and Ubuntu have booted properly for me. Thanks for all the help and I'm excited to be using Linux!

---

### Post by jcronkhite on 2007-07-19
That's great news!  I hope my limited info help.  Enjoy Ubuntu!

Edit: I saw this on Digg today - [http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty]("http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty")

Might help someone who later stumbles onto this thead.

---

