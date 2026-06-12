---
title: "Is it actually possible (necessary?) to defrag?!"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by teHIngo on 2007-04-29
Simple question ;)!

See topic title :popcorn: !

---

### Post by jondecker76 on 2007-04-29
i've been wondering the same thing...

---

### Post by jmartrican on 2007-04-29
An Uber admin I know said no.  He said that over time Linux will shift data around so that defrag is not needed.  Say there is 5 megs of free disk space (which is sitting between two files), if you need to write a 7 meg file, instead of wrting 5 in the free space and 2 somewhere else, Linux might shift the files sorrounding the 5 free megs so that there is 7 megs avail.  This is how it was explained to me.  The explanation did not contain large disparities (100 megs when only 5 is avail in a free spot).  I'm assuming ext2/3 filesystems... don't know if that makes a diff.

---

### Post by Old Pink on 2007-04-29
There should never be a need to defrag, jmartrican explains it rather well.

Should you feel an uncontrollable need to defrag, for some crazy reason, head into Synaptic and search for defrag. (Or, go to terminal and type:```
sudo aptitude install defrag
```)

There are tools available. :)

---

### Post by sasquatch74 on 2007-04-29
As a previous post says, no, you do not have to defrag.  
There is a description how a linux system allocates files here: [http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting]("http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting")
I believe I have read that there is a defrag program available for linux, but that most people will never need to use it.  

Cheers!

---

### Post by bluevoodoo1 on 2007-04-29
Hmm... I never thought it was possible...

ext3 for example : "...A true defragmentation tool does not exist for ext3..."

[http://en.wikipedia.org/wiki/Ext3#Defragmentation](http://en.wikipedia.org/wiki/Ext3#Defragmentation)

---

### Post by Tomosaur on 2007-04-29
Contrary to popular belief - Linux filesystems **do** fragment, but only when the disk is nearly full. Generally, Linux tries to keep files contiguous (ie, all together rather than sliced up and stored all over the place). While this can theoretically lead to a drop in performance in some areas (eg, boot times may be slower if the various boot scripts are stored in different places in your hard drive), **overall** drive-read performance should be very quick compared to a filesystem which fragments regardless of free-space left (such as NTFS). It is also possible, I suppose, to optimise your hard drive similar to how Windows does - ie keeping boot files together, important system files together, etc etc - and thus gain the same or similar performance which Windows is supposedly good for.

When your hard drive comes close to full (ie, you have little free space left) - Linux has no choice but to begin fragmenting your files so that they fit in whatever space it can find.

---

### Post by teHIngo on 2007-04-29
Great, thanks for your very good answers :)!

---

