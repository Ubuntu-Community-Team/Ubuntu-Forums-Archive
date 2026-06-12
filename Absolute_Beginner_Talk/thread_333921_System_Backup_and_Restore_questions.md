---
title: "System Backup and Restore questions"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by andytof47 on 2007-01-08
Hi i would like to ask about the system backup utility that automatix2 installs

first of all

I have a heap of time invested in my current setup

due to the amount of experimentation that was invovled in the setup of beryl ati drivers mac osx
theme and the like

so i want to back up but instead of using Ghost i want something that does the same idea but doesn't neccisarily have to be an "image" per se'

I heard there is a utility built into linux that does something like this and wondered if anyone had used it??? what type of success i might expect with it - e.g if i had to reinstall do i just restore the file???? 

cheers

---

### Post by xyz on 2007-01-08
Hi,
You may want to try this:
[Howto: Backup and restore your system!]("http://ubuntuforums.org/showthread.php?t=81311&highlight=backup+windows+drive")
OR
[Use Partimage]("http://www.psychocats.net/ubuntu/partimage")
Both have worked fine for me. There are other ways to back up as well.

---

### Post by andytof47 on 2007-01-08
thanks xyz check it out ;)

---

### Post by andytof47 on 2007-01-09
I am just wondering then about the backup technique using the .tar method.

Since it is not an image per se' could I load Ubuntu on another system and then use this backup to "restore" all of my settings on that system

so essentially it is cloned but without the hardware information - could that be done? I would love it if it was:p 

cause it ususally takes weeks for me to get my system to that Just Right status - I am imagining something wonderful - hopefully doable

---

### Post by xyz on 2007-01-09
One thing I know -and there's surely another way to do it- is that you can save/copy your backup on an external HD, CD and then reinstall your very same config in your 2nd box which would have Ubuntu installed in it.

You'll be able to "see" your backup in Nautilus in 'File System' as root using the tar method.
So, in your 2nd computer with Ubuntu installed, you'll also need to copy your backup in 'File System' as root. Then running the HowTo's restore command will get you the same config there as in your 1st box.

Now I have never tried this myself but you might just want to have a look at it:
[Restoring with YOUR installed packages as well]("http://forum.ubuntu-fr.org/viewtopic.php?id=64855")
thus avoiding to spend lots of time looking/reinstalling your favorite packages.
This is located on the French Forum..so if you need help with the language, let me know.
But the command lines to run are in English.

---

### Post by andytof47 on 2007-01-09
cheers for the extra method i will try it on my laptop soon.....

I tried it on my desktop and it kind of worked - but things like gdesklets weren't installed and some other things bu it think it could have been the desktop itself   (faulty lemon):mad: 

I have done a backup with the tarball maethod and I am going to try installing the "image" on a fresh lappy disk 


thanks

---

