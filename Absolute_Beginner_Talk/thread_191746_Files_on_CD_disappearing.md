---
title: "Files on CD disappearing?"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by the_FNG on 2006-06-07
It's kinda hard to phrase my question, but it's almost like my cdrom is playing tricks on me.  At the time I was copying over files from CD to a directory for Quake4, changing discs as necessary (using this sexy GUI, because I'm new, lol).  When I got to the few remaining files, it seemed like my cdrom wasn't seeing all the files.  Even in the terminal something seems odd.  Like I can't see directories, or certain files. This is what I get:

```
fng@fng-desktop:/media/cdrom$ ls -a
[COLOR="RoyalBlue"].  .. [/COLOR] [COLOR="Lime"]AUTORUN.EXE  AUTORUN.INI  Quake4_disk.exe  quake4.ico[/COLOR]
```

Is my drive not mounted correctly?  Do I not have the correct permissions?  I'm a little confused here.

Thanks folks.

---

### Post by mscman on 2006-06-07
I'm glad someone else mentioned this!  I had forgotten about it.  This happened to me earlier today when I was making copies of some data CDs we use in the lab.  After copying a few, the CD that I put in only showed a few of the files.  I ended up having to restart in order for the files to be displayed again.  Not really sure how to go about troubleshooting this...

---

### Post by the_FNG on 2006-06-07
Seems this fella was having similar issues a week ago: [http://www.ubuntuforums.org/showthread.php?t=183682&highlight=cdrom](http://www.ubuntuforums.org/showthread.php?t=183682&highlight=cdrom)

I tried his suggested work around and all seemed fine.  Looks like it's related to automatix and the eject button.  It seems that not using the eject button on the drive itself, is the (temporary?) solution.

hmmm...  okie dokie...  no biggie.

---

### Post by mscman on 2006-06-08
guess i'll stop doing that then!  glad someone was able to track down the source.  thanks! =D>

---

