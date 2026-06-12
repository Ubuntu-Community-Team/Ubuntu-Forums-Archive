---
title: "does ubuntu save deleted files from flashdisk?"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by v_villaver on 2007-08-13
i'm just wondering if i delete files from my external memory (flashdisk)without even opening the file, will ubuntu still save that file in the computer memory from my flashdisk? 

or is it like Windows that if you erase files from a flashdisk, it disappears forever and does not go to recycle bin?

i deleted some personal files from my flashdisk using ubuntu at work and i dont want my office computer to have any of my personal files.

help!

i read in the other threads ([http://ubuntuforums.org/showthread.php?t=510769](http://ubuntuforums.org/showthread.php?t=510769)), they say you cannot completely delete files from ubuntu not unless the memory gets full so it will go to the beginning. cannot completely understand this. pls explain in layman's terms.

---

### Post by iver2435 on 2007-08-13
When I delete files from my thumbdrive, it creates a .Trash folder on the thumbdrive that stores all my deleted files.

Any file or directory with a "dot" in front is a "hidden" directory in Ubuntu, so you may have to do a long directory listing to see it  (ls -la).

If you delete the files out of that directory, they're gone.

In terms of never being able to "truly" delete files, basically when you delete a file, the operating system (Ubuntu in this case) will mark that file in a special way that hides the file from view and allows that file's place on the hard disk to be overwritten.  So, in the strictest sense, no files are ever really "deleted", just merely "reclassified".  Now, if you had a utility that could "unmark" those files as deleted files (which many vendors have done over the years) you can get back that file in it's entirely.  The only way to "truly" delete a file is to delete it the normal way, and then write over that file's place on the hard disk with either another file or bogus information.  There are utilities in almost every operating system to do such a thing, so fire up Google and search for "file shredders" or "file nukers" or something like that and you'll find what you're looking for.

---

### Post by bodhi.zazen on 2007-08-13
Yes, and sometimes it will save the files in your home directory ($HOME/.Trash) or if you deleted the files as root, in  /root/.Trash

HTH

---

### Post by eentonig on 2007-08-13
did you delete from the CLI?

> **rm** <filename>

Or via Gui?
The Gui does creates a hidden folder called ".Trash" on the volume where you deleted the files.

---

### Post by Hospadar on 2007-08-13
If you did "rm" from a terminal, you are unlikely to be able to get those files back.

---

### Post by stchman on 2007-08-13
> **v_villaver said:**
> i'm just wondering if i delete files from my external memory (flashdisk)without even opening the file, will ubuntu still save that file in the computer memory from my flashdisk? 

or is it like Windows that if you erase files from a flashdisk, it disappears forever and does not go to recycle bin?

i deleted some personal files from my flashdisk using ubuntu at work and i dont want my office computer to have any of my personal files.

help!

i read in the other threads ([http://ubuntuforums.org/showthread.php?t=510769](http://ubuntuforums.org/showthread.php?t=510769)), they say you cannot completely delete files from ubuntu not unless the memory gets full so it will go to the beginning. cannot completely understand this. pls explain in layman's terms.

Yes, by hitting the delect key in Nautilus will create a .Trash folder on your USB thumb drive.  you  will then have to delete the files in the .Trash.

One way to permanently is to do a Shift-Delete after highlighting the file.

---

