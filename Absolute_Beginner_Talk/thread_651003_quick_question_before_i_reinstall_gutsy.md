---
title: "quick question before i reinstall gutsy"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by Sonic Reducer on 2007-12-27
i think i messed up my gutsy install by running an AVG scan on it (i used [Ext2FS]("http://www.fs-driver.org/") on my root and separate /home partition). i ran the scan and a bunch of things were listed as "change", i killed the scan and tried to boot into gutsy. i *tried*.

after doing an install yesterday on my parents computer (they were using dapper still, and i upgraded) i noticed that if i manually edited the partition table (i think thats how they put it, its the option where you can decide to resize an existing partition, use the entire disk, or the option i'm talking about) i could select which partition to mount as /, and i saw i could select which partition to use as /home.

if i reinstall gutsy tonight, will i lose all my data i have in my /home? i have a lot of music, movies, and things i can't mention on a family-friendly forum on my /home partition (i'm just going to refer to all music, papers, etc. as "my documents" from now on). i know things like configuration settings, program folders, and other OS-related files and folders should be overwritten, but will it erase things not pertaining to the installation?

i feel like i am not being clear enough, so i'll try an anecdote:

every six months or so my computer would need a fresh install of XP. when i reinstalled XP and rebooted all my documents were still there untouched, and all the corrupted system files and folders were fixed. is this what would happen if i manually edit the partition table?

i would check the "Format" box next to the partition i want gutsy installed in, and select the partition i have all my documents in to mount as /home, but would not select to format it.

also, while i have someone who knows about linux, what would be the best way to make my ext3 files visible but read-only in XP? i got an xbox 360 and like to stream music to it but there is no easy way to do it in ubuntu.

it would also be cool to hide files prefaced with a dot so i don't have to wade through all my configuration settings to get to my music folder in /home

---

### Post by kpkeerthi on 2007-12-27
> 
if i reinstall gutsy tonight, will i lose all my data i have in my /home?

No.. when you choose NOT to format it.

---

### Post by Sonic Reducer on 2007-12-27
> **kpkeerthi said:**
> No.. when you choose NOT to format it.

so marking it as /home without marking the format will preserve every file that isn't getting overwritten?

then if i run ```
sudo apt-get autoremove
``` it will remove the files and folders from programs that were installed from the last install of gutsy but are not installed on this one (that are also probably corrupted from the AVG scan) right?

i'm sorry i'm sounding repetitive, but i got a lot of quality "movies" and a lot of music i don't want to have to re-rip on that partition

---

### Post by kpkeerthi on 2007-12-27
Ubuntu does not "install" anything in /home. 

When you reinstall Gutsy, let the installer reformat all your partitions but keep your existing /home partition. This would effectively erase all the applications you had in the previous install. The installer reinstalls the stock applications that come included in the CD. 

From now on, any **apt-get install **or **apt-get remove** will affect the new installation (because last installation is now gone as you have instructed the installer to reformat your root partiion). The document and videos in your /home should remain as they were before (because you instructed the installer not to reformat it).

---

### Post by bone2006 on 2007-12-27
you'll find the installed configuration in your home directory.  They are hidden folders with a period in front of them.  Just click show hidden folders in naitiuls or konqueror to see them

---

### Post by Sonic Reducer on 2007-12-27
> **kpkeerthi said:**
> Ubuntu does not "install" anything in /home. 

When you reinstall Gutsy, let the installer reformat all your partitions but keep your existing /home partition. This would effectively erase all the applications you had in the previous install. The installer reinstalls the stock applications that come included in the CD. 

From now on, any **apt-get install **or **apt-get remove** will affect the new installation (because last installation is now gone as you have instructed the installer to reformat your root partiion). The document and videos in your /home should remain as they were before (because you instructed the installer not to reformat it).

i mean the folders in my /home directory from programs i have installed. for example, i have conky installed on my computer, and .conky.rc is in my home folder. if i autoremove will it remove the folders and files from programs in my /home that are from the previous install? (like delete .conky.rc if conky isn't installed yet)

.:EDIT:. you know what i think i'll do? i'll just delete everything but my documents in my /home partition when i'm using the live CD. that way i don't have to worry at all.

---

### Post by kpkeerthi on 2007-12-27
> 
i mean the folders in my /home directory from programs i have installed. for example, i have conky installed on my computer, and .conky.rc is in my home folder. if i autoremove will it remove the folders and files from programs in my /home that are from the previous install? (like delete .conky.rc if conky isn't installed yet)

No everything in your home will be retained as such.

---

### Post by Sonic Reducer on 2007-12-27
turns out the folders were corrupted too, i lost everything.

i have a partial backup or stuff, but i guess i learned my lesson

---

