---
title: "ADEPT package management"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by venik212 on 2007-12-06
Is there anything wrong with ADEPT?  I found strigi (a desktop index/search engine) installed on my machine (I did not ask for it to be installed-- I think it came with 7.10).  Since it was working intermittenly, I removed it with ADD/REMOVE programs.  I search the directories and found that it was still on my machine, so I used ADEPT to remove (purge) it.  It was still around, with its 0.5 gb database.  I used the Konsole to unistall it with aptitude, but it is still around.  I do not want to simply *erase* strigi from the disk, for fear it might still be connected to something important.  Strigi DID disappear from the K menu.  I tried "sudo aptitude update" but it did not help.
So here are my questions:
1) Why didn't the removal take effect?
2) What do I need to do to reclaim all that disk space without screwing up something important?
3) Why aren't the various installation-removal mechanisms playing nicely together?

---

### Post by asmiller-ke6seh on 2007-12-06
Could it be that what you are seeing is the configuration and database files?

You might want to simply try renaming the folder/files and see if that allows your system to work okay ... and THEN delete the files , afterwards, if there is no problem.

What is the name of the folder holding these files? and where is it located - you said that the application was not in the K Menu.

BTW, I am a Gnome user, so I am not familiar with that app, or its installation/deletion.

---

### Post by Hospadar on 2007-12-06
If there was some indes in your home folder, no uninstallation would remove this.  if it's in your home folder, just delete in manually.

Which and where exactly are the files still on your system?

---

### Post by venik212 on 2007-12-07
The files are named something like:
/home/udi/.strigi/clucene/_35pz.cfz
They take up 500 mb!
The installation files are there, but they are not the ones I want to remove.

---

### Post by g2g591 on 2007-12-07
"if it's in your home folder, just delete in manually" as said above. /home/udi is your home folder so go ahead and delete them

---

