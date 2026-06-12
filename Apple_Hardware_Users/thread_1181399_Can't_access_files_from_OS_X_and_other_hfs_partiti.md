---
title: "Can't access files from OS X and other hfs partition while using Linux"
date: 2009-06-07
forum: Apple Hardware Users
---

### Post by afrotman on 2009-06-07
I'm currently using Ubuntu 9.04 and Mac OS X (dual boot) on my MacBook 4,1 and I have three partitions on my hard drive: one is hfs (Mac), ext3 (Linux) and a seperate hfs partition. The problem is I can't access certain files on the hfs partitions when using Linux. I'm not completely locked out, I can access the partitions but once I get to the user file in my partition for OSX, I can't acces files like documents, public, music, video and in the other partition (which contains all of my music) I can't access the music file, a box comes up saying I don't have the permission to view it. I've gone onto Mac OS X and change the privileges on all of my files to everyone read/ write. I've tried becoming the root user but I think i'm doing something wrong. I've been working on this for hours and searched for multiple answers but nothing seems to work. I need help.

---

### Post by cyberdork33 on 2009-06-07
When you change the permissions to allow everyone to read/write, you have to make sure you apply to all files and subfolders.

---

### Post by afrotman on 2009-06-08
I have done this thats the problem. I don't have any idea what the problem is, i'm up $h!t creek without a paddle

---

### Post by MikeTheC on 2009-06-08
Well, what files exactly are you trying to access?

EDIT:

If you can evacuate your non-system HFS partition of files (temporarily) I'd suggest you install MacFuse and then nuke-n-pave that partition and format it as NTFS. With MacFuse installed you'll have full read/write access in Mac OS X, and of course Linux has full read/write support for NTFS.

Bear in mind that it's up to Apple to decide to play nicely with Linux or not. Thus far, it's a schizophrenic relationship at best.

---

### Post by cyberdork33 on 2009-06-08
> **MikeTheC said:**
>  Bear in mind that it's up to Apple to decide to play nicely with Linux or not. Thus far, it's a schizophrenic relationship at best.
full specs for hfs+ are published. It is Linux that has poor support for the filesystem...

Either way, it is a permissions issue, though I don't know why modifying the permissions isn't working.

---

### Post by afrotman on 2009-06-08
I did download MacFuse and originally tried to do my seperate partition as NTFS but OS X wouldn't recognize it. Granted the site says its servers were down but MacFuse downloaded just fine. I'm trying to access a regular folder that I created (didn't copy from OS X) that I labeled Music with all of my music from my iTunes folder in it.I have no idea what to do, I've searched this site and many others but every time I tried a plausible solution It doesn't work.

---

### Post by afrotman on 2009-06-08
Oh by the way MikeTheC love your location, great series, It amazes me how an author can create an entire plot line off of a bad pun. This is complete off-topic of course haha

---

### Post by afrotman on 2009-06-08
Problem mostly solved, I changed the access on my seperate partition from no access to read/write and restarted it a time or two and i'm set with my seperate partition OS X is a different story but I'm satisfied thanks for your help.

---

### Post by MikeTheC on 2009-06-08
> **afrotman said:**
> Oh by the way MikeTheC love your location, great series, It amazes me how an author can create an entire plot line off of a bad pun. This is complete off-topic of course haha

Thanks! To date, you're the first person to get it.

And yes, Xanth is quite the hilarious, pun-laden trip, isn't it?

---

### Post by Musicnut on 2009-06-16
Please excuse me if I break any rules by my "replying" to this thread with my question. I rarely post in forums.
 
I will confess that I loaded Ubuntu (based on a suggestion that was posted elsewhere) in an attempt to recover data from a HDD that was in a MacBook. (Customer spilled coffee in it and fried the mainboard)
 
It worked GREAT except for the fact that I can't access the folders that I need to be able to copy. I need the documents, music, pictures etc from the main user's folder and am told that since I'm not the owner, I can't access them.
 
This is a SATA drive that was loaded while it was in the MacBook. It is not a partition created after the fact in the machine that I loaded Ubuntu on.
 
Can someone offer a solution? If it were a PC I would just take ownership of the drive and be done with it. What I need to copy is videos of the guy's daughter that he has no backups of. Corrupting these files to a point where there is no recovery is not an option.
 
If you have an answer for me please type slowly. I don't read very fast. ;)

---

### Post by cyberdork33 on 2009-06-16
> **Musicnut said:**
> Please excuse me if I break any rules by my "replying" to this thread with my question. I rarely post in forums.
You should start a new thread if you have an issue of your own.
 
> **Musicnut said:**
> I will confess that I loaded Ubuntu (based on a suggestion that was posted elsewhere) in an attempt to recover data from a HDD that was in a MacBook. (Customer spilled coffee in it and fried the mainboard)
 
It worked GREAT except for the fact that I can't access the folders that I need to be able to copy. I need the documents, music, pictures etc from the main user's folder and am told that since I'm not the owner, I can't access them.
The issue here is that you cannot change permissions on the filesystem because it is read-only. You need to open an application with root permissions in order to access any files on the system. You can start a root nautilus file browser with the command 'gksudo nautilus' you can then navigate to the files you want to access within that window. You may need to open a second root nautilus browser to copy the files to another location. In that new location, you should be able to modify the permissions on the files.
 
  > **Musicnut said:**
> If you have an answer for me please type slowly. I don't read very fast. ;)
If you need more help, just ask.

---

