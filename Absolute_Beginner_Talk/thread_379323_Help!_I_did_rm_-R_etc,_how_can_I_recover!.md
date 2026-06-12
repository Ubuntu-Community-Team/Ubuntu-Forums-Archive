---
title: "Help! I did rm -R /etc, how can I recover!"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by Crashmaxx on 2007-03-08
I was trying to clean up the leftover config files from some packages I removed last night. I was doing tab completion and hit enter with sudo rm -R /etc/ displayed and therefore, deleted my whole /etc! I had a lot of important config in there.

How can I best recover from this? Its a 6.06 server with a RAID 5 setup with LVM on top and a big root partition that's ext3. Redoing the config changes isn't the end of the world, but I mean I lost stuff like /etc/passwd and /etc/fstab all of that. I did a hard shutdown right away so it wouldn't write over it. But ext3 zeros out inodes, and it is a lot of files. Is there some command I can do in the system rescue cd to find all files that were in /etc and save them? I tried doing strings on the whole partition and saved it to a file, but I think it only found non-deleted files.

Any help undeleting this en mass? Or any help recreating the default files at least?

Is recovering the files or just booting up and trying to remake the files the better option?

---

### Post by melancholeric on 2007-03-08
[http://linux.sys-con.com/read/117909.htm](http://linux.sys-con.com/read/117909.htm) might help. No, it's not going to be easy.

---

### Post by Perfect Storm on 2007-03-08
Might better to do a clean install.

---

### Post by dannyboy79 on 2007-03-08
if you don't have a backup that you can restore, I would say just pop in the live cd and copy the /etc from the cd onto your hard drive and then start editing BUT i don't see how it's going to work for config files that you're not even sure you had. I would say a clean install is order here and then once you're done getting your system back to the way you had, BACK IT UP.

---

### Post by Perfect Storm on 2007-03-08
...and have seperate /home for the rest of te system is also a good idea.

---

### Post by Crashmaxx on 2007-03-08
Well, after some messing about, I went ahead and did a clean install. Luckily there was no data on the server yet, but resetting up everything will be a pain.

So  this time I made a seperate /home and now I need to get ssh setup again. Then I can redo all my basic stuff, then I'll get a backup script setup so I can back it all up to my network drive.

Fun, fun, fun :(.

---

### Post by dannyboy79 on 2007-03-08
it's probably safest to use a tool that backups your data while it's not running although it should work either way. my signature has a great tool for this and it works to use a netowork drive as the destination for the image. I use partimage every once in awhile but I use sbackup which is envoked by cron which backs up my entire system incrementally everyday at 2am. (this means it only backs up what changed) then I do a full backup, everything no matter what, once a week. all this can be done using sbackup. it was created when gogle had that summer of code thingy. good luck to ya

---

### Post by Crashmaxx on 2007-03-09
I use sbackup on my laptop, it works nicely. But it requires GUI, or at least has a lot of dependentcies from it. So I finally got simplebackup setup. Its similar to sbackup, but is really just a perl script. Worked great, after a lot of tweaking. Gives all the employess access to a daily zip of all the changes that day. Just what I needed.

---

