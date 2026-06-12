---
title: "Backing Up Home Folder"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-09-07
I'd like to back up my Home Folder onto a Thumb Drive.
I tried to copy my entire home folder over but it gave
me a few " can not copy " warnings during the process.

Do I need to be Root to do this?
What am I doing wrong?

Thanks  :KS

---

### Post by Dr Small on 2007-09-07
I would try Root as my second guess.

---

### Post by expatCM on 2007-09-08
Which files are giving you the problem ...?   I think several items are going to be in use ... you may want to boot from the Live CD and then copy...

---

### Post by banewman on 2007-09-08
There are hidden config files in your /home directory. Open it and click -view-show hidden files. If you are copying your /home directory completely these files will be being used and errors will show up.  I would open /home and open the thumb drive on the desktop at the same time and copy the relevant files over by right click-copy  - right click-paste, then use rsync to update the files from then on. Hope this helps. :)

---

### Post by Orbital75 on 2007-09-08
I'm sure you guys are correct. The errors I am getting have to be from config files that
are in use. From what I get, its the .Invisible files that are causing the errors. I'm copying 
the entire folder over ( Not Home ), just My Home folder ( ME ). I can see these invisible files and
folders when I choose to show them.  Humm.... How does one normally back these up?
Isn't there certain protocol to follow? Aslo, what is rsync?  is it similar to Sync Toy for WinXP?

:KS

---

### Post by JimmyBEng on 2007-09-08
When I back my home directory, I just tar and zip the whole thing.  I do the configurations as well because then I can restore any of those if I ever need to.  A common one that I have used before is the .mozilla-thunderbird folder which holds all of my email. 

Easy way to make an archive:
-Open /home in nautilus
-right click on your home folder
-select Create Archive

This will open a window that will let you create an archive of your whole home folder. I usually save it to my other data partition, but you could probably save it straight to your USB drive

---

### Post by kane77 on 2007-09-08
there are couple of tools you can use...

there is Home user backup and home user restore (hubackup package) which seems to do the job...
there is also simple backup/restore, that I found realy useful when I was programming and needed to backup regularly.. it backup at given interval only the files that were changed and you can set up how much to keep (for example you can keep all the backups from today and two per day from previous etc...)...

---

### Post by Orbital75 on 2007-10-11
Thanks guys, those are good tips.....

---

### Post by Bruce M. on 2008-01-27
> **kane77 said:**
> there are couple of tools you can use...

there is Home user backup and home user restore (hubackup package) which seems to do the job...
there is also simple backup/restore, that I found realy useful when I was programming and needed to backup regularly.. it backup at given interval only the files that were changed and you can set up how much to keep (for example you can keep all the backups from today and two per day from previous etc...)...

I do NOT recomend HUB at all:

HUBackup - works fine - but very slow.
HURestore - ***doesn't even open***, so you have to use DAR to get your files back.

---

### Post by mortsahl on 2008-01-27
Unlike Windows, linux will copy (or delete) files that are in use.  Your problem is likely that some of the files are owned by root.  Best way to copy the files to you thumbdrive is to cd to /home then ...

sudo cp -rf * <thumbdrive>

I also like another suggestion here ... tar or zip them ... make sure you run it from sudo, tho

---

