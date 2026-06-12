---
title: "Formatting External hard drive"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by estin on 2007-12-25
i just got a new external hard drive (250gb) for backing up from my laptop and sharing files between my friends Windows xp machine.  The drive is currently formatted as NTFS which hasn't been a problem for me reading or writing to.  I'd like to just re-format it as NTFS to clean whatever factory software it has off it.  i keep seeing to use Gparted but i can't find it anywhere in my programs and ubuntu tells me its already installed.  any clue?

---

### Post by adam.tropics on 2007-12-26
<ALT><F2> 
```

gksu gparted
```

edit:although it should be in you menu as system-->administration-->partition editor

---

### Post by estin on 2007-12-26
oh thanks much, completely missed that one.  alright well my next question is how to get it to format NTFS.  the option for it is grayed out.

---

### Post by kpkeerthi on 2007-12-26
Use either of this. I prefer System Rescue CD. 
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
[http://www.sysresccd.org/](http://www.sysresccd.org/)

---

### Post by LaRoza on 2007-12-26
To format something as NTFS, use Windows. It is the simplest and easiest way.

---

### Post by adam.tropics on 2007-12-26
or just unmount it and no need for live cd. I belive though to format ntfs  via gparted may require you to install ntfsprogs. It's in the repos. I think either that being missing, or the partition being mounted, would be why your options are grayed out.


edit: LaRoza.....dead right there

---

### Post by LaRoza on 2007-12-26
> **adam.tropics said:**
> 
edit: LaRoza.....dead right there

Of course, I don't get paid for being wrong. :)

---

### Post by estin on 2007-12-26
> **LaRoza said:**
> To format something as NTFS, use Windows. It is the simplest and easiest way.

yeah that would be great and all but i don't have access to a windows machine at the moment.

---

### Post by LaRoza on 2007-12-26
> **estin said:**
> yeah that would be great and all but i don't have access to a windows machine at the moment.

I see, maybe your friend could do it? 

(Sorry, I just looked at the post and saw you didn't have the XP installation.)

---

### Post by adam.tropics on 2007-12-26
> **LaRoza said:**
> Of course, I don't get paid for being wrong. :)

lol...and there were we thinking you did this out the goodness of your heart!!

---

### Post by LaRoza on 2007-12-26
> **adam.tropics said:**
> lol...and there were we thinking you did this out the goodness of your heart!!

I didn't say I got paid, just that I didn't get paid for being wrong.

I am a bot, actually.

---

### Post by estin on 2007-12-26
well i decided screw it and went to format it as ex3 and now theirs a folder called "lost+found" and it won't let me delete it.  it says i'm not the owner and i don't have permission to view it or modify.  LOL i'm kinda stuck, i never had this much hassle formatting a drive before.  i even deleted the old parition, create and formatted new and its still there.  :confused:

edit i wanted to mention i decided not to use ntfs because i would delete things from the hdd and it wouldn't free up the space.  the files were gone but the space was still in use.

---

### Post by LaRoza on 2007-12-26
> **estin said:**
> well i decided screw it and went to format it as ex3 and now theirs a folder called "lost+found" and it won't let me delete it.  it says i'm not the owner and i don't have permission to view it or modify.  LOL i'm kinda stuck, i never had this much hassle formatting a drive before.  i even deleted the old parition, create and formatted new and its still there.  :confused:

edit i wanted to mention i decided not to use ntfs because i would delete things from the hdd and it wouldn't free up the space.  the files were gone but the space was still in use.

You would have had to emptied the trash: .Trash to free the space

Don't worry about lost+found, leave it alone.

---

### Post by estin on 2007-12-26
> **LaRoza said:**
> You would have had to emptied the trash: .Trash to free the space

Don't worry about lost+found, leave it alone.

well what is it? if i have my friend re-format this to ntfs will it be gone? does that matter?
thanks for all your help man.

---

### Post by LaRoza on 2007-12-26
> **estin said:**
> well what is it? if i have my friend re-format this to ntfs will it be gone? does that matter?
thanks for all your help man.

It will be gone if it is reformated.

If you want a file system Windows can use, try FAT32. You won't be able to store large files on it (4 GB - 1 byte is the limit)

I am not exactly sure what lost+found is, but it is always present on ext3.

---

