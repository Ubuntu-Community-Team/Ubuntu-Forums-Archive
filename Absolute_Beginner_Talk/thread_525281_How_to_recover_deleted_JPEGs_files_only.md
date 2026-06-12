---
title: "How to recover deleted JPEGs files only"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by rubab on 2007-08-14
I dont know how to recover deleted JPEG files from ext3 file system . I am a newbie that is why i am a bit confused with the terminal. The files were in a folder inside my home folder . I just want to recover the files from that specific folder.

I searched the forum but didnt find anything on how to recover a folder with JPEG files.

Help please.

---

### Post by indytim on 2007-08-14
If the files are not in your trash, then they are probably gone.  Adequate backups help to avoid future mishaps... sorry.

IndyTim

---

### Post by BaffledMollusc on 2007-08-14
Is the folder in your trash? (Click on the trash icon in the bottom right of the screen, on the taskbar.)

---

### Post by rubab on 2007-08-14
"Is the folder in your trash? (Click on the trash icon in the bottom right of the screen, on the taskbar.)"

No the folder is not in my trash can.

---

### Post by lgambett on 2007-08-14
It is very hard (not to say impossible) to recover erased data from an ext3 volume. It is no way as simple as under NTFS or FAT32 file systems.

---

### Post by BaffledMollusc on 2007-08-14
> **rubab said:**
> "Is the folder in your trash? (Click on the trash icon in the bottom right of the screen, on the taskbar.)"

No the folder is not in my trash can.

If you delete files using the Nautilus file browser, they go to the trash and can be recovered. If you delete files from the terminal using the "rm" command they're gone forever - no recovery.

---

### Post by az on 2007-08-14
Stop using your computer immediately!  Your data is still there until something overwrites it!

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Use foremost or photorec.  Specify jpeg or you will end up with too many files.

Boot a live cd (the Ubuntu installer or Rescubuntu (rescubuntu.info) ) and run them from there.  You will need another hard drive that is big enough to put all the recovered files.

---

### Post by Paul820 on 2007-08-14
Somebody will have to write something for recovering files on linux in an easier way. With linux getting more and more popular people are going to need an easier way to recover files from their drives. Windows has loads of file recovery programs, i used to use pc inspector file recovery which was free. Surely someone can write something like that for linux?

---

### Post by aquavitae on 2007-08-14
> **Paul820 said:**
> Somebody will have to write something for recovering files on linux in an easier way. With linux getting more and more popular people are going to need an easier way to recover files from their drives. Windows has loads of file recovery programs, i used to use pc inspector file recovery which was free. Surely someone can write something like that for linux?I agree, but even without that, why not change the rm command to mv ~/.trash?  It should be quite easy for the ubuntu developers to include a small script (or even just an alias) in the distro that does this.  Then even if someone does use rm, at least it goes to the trash.

---

### Post by nvrpunk on 2007-08-14
sudo apt-get install testdisk

sudo photorec

This program will allow you to recover just deleted images or other file types.  Even on ext3.  You could also grep your drive.  But this is much easier.  

-nvrpunk-

---

### Post by wirelessmonkey on 2007-08-14
But what happens when I want to empty the trash? ;P

---

### Post by newmo on 2007-08-14
> **aquavitae said:**
> I agree, but even without that, why not change the rm command to mv ~/.trash?  It should be quite easy for the ubuntu developers to include a small script (or even just an alias) in the distro that does this.  Then even if someone does use rm, at least it goes to the trash.

I like having the choice of a full-on "complete delete" using rm at the commandline and the standard GUI delete with failsafe option that I am used to in Windows.

That said it wouldn't hurt to reiterate that rm is a bit dangerous - most of the info I looked at when learning basic commands pointed this out anyway.

> You could also grep your drive. But this is much easier. 

-nvrpunk- 

Grep your drive eh?  It hadn't occurred to me that it would still be visble to the OS in that way.  I feel some experiments coming on.

---

### Post by rubab on 2007-08-14
I need an Example of this

Usage: photorec [/log] [/debug] [/d recup_dir] [file or device]

/log          : create a photorec.log file
/debug        : add debug information

What should i use [file or device] in this place.
It would be helpful if you give an example.

---

### Post by asmoore82 on 2007-08-14
> **wirelessmonkey said:**
> But what happens when I want to empty the trash? ;P

```
~ $ /bin/rm -rf ~/.Trash/*
```

:KS

---

### Post by rubab on 2007-08-14
It says
You do not have the permissions necessary to view the contents of "recup_dir".

---

### Post by nvrpunk on 2007-08-14
You have to run photorec under sudo to access the device.  Just photorec with no option will work then you must choose the device.  The reason you cannot access the folder is that it was created as root under sudo.  

sudo chmod -r 755  /whatever/folder   

sorry for the delayed reply, I am at work in Iraq :)

this command stand for modify permissions, -r recursive meaning all subfolders.  755 is the standard for most files and folders.  

there is also chown for change owner.  man chown or man chmod to learn more :)

---

### Post by az on 2007-08-14
I don't suggest installing testdisk on this drive.  Any file you download or run may overwrite deleted data!  Use testdik from a live cd instead!  Anyway, anything you save to the disk you are recovering from will possibly overwrite your unsaved data.

You absolutely need an extra storage medium here.

> **Paul820 said:**
> Somebody will have to write something for recovering files on linux in an easier way. With linux getting more and more popular people are going to need an easier way to recover files from their drives. Windows has loads of file recovery programs, i used to use pc inspector file recovery which was free. Surely someone can write something like that for linux?

All the tools are there.  I guess you are talking about a nice GUI for them.  Go ahead and write one!  No one is stopping you...  

No one would be against the idea.  The reason it hasn't been done yet is because there is not enough demand.

> **newmo said:**
> 
Grep your drive eh?  It hadn't occurred to me that it would still be visble to the OS in that way.  I feel some experiments coming on.

Use the sleuth kit to make an image of the unallocated space and then recover the data from that image.

---

### Post by nvrpunk on 2007-08-14
True, you shouldn't run photorec unless you have another drive to save the recovered data to.  

I was assuming a base level of knowledge, although the likelyhood of actually overwriting existing data is slim unless your drive is full.

---

### Post by rubab on 2007-08-14
Thanks for your help

---

### Post by wirelessmonkey on 2007-08-14
> **asmoore82 said:**
> ```
~ $ /bin/rm -rf ~/.Trash/*
```

:KS

Ah, but his hope would be that rm was remapped to mv ~/.Trash, so you'd end up with this scenario:

"mv ~/.Trash ~/.Trash"

My comment was a joke ;)

---

### Post by aquavitae on 2007-08-15
> **newmo said:**
> I like having the choice of a full-on "complete delete" using rm at the commandline and the standard GUI delete with failsafe option that I am used to in Windows.I agree - I like being able to completely delete something, but scripts are customisable, so it wouldn't necessarily be fixed.  In any case, it would be easy to add an option to permenantly delete something, e.g. rm -x ...  I actually had a script to do that on my old system (gentoo) but I haven't bothered in ubuntu cos I use the gui more.  I think I need to resurrect it though...

---

