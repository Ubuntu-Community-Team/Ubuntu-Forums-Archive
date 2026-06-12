---
title: "JPG Problems"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by yagiska on 2007-03-28
i'm having a problem with my jpegs. here's my scenario:

i was running windows xp, and backed up my jpgs to another hd.

installed ubuntu desktop on my desktop
installed ubuntu server on my server and then added the desktop package (no flames for running a gui on my server)

both are running edgy

moved the jpgs back from the ntfs hd to the server hd

opening jpgs (or their properties) works fine on the server

opening those jpgs (or their properties) via the nfs mount from my desktop causes nautilus or eog to crash

copying the file to the local hd does NOT fix the problem

thumbnails display fine in nautilus, however

the files open fine in gimp or f-spot

here are the details from the crash dialog:

[http://www.ubuntuforums.org/attachment.php?attachmentid=28407&stc=1&d=1175058557](http://www.ubuntuforums.org/attachment.php?attachmentid=28407&stc=1&d=1175058557)

all instances of (no debugging symbols found)
have been replaced with -
to save on file size


Thank you
Kris

---

### Post by profXavier on 2007-03-28
What file system type is your ubuntu install on?

---

### Post by yagiska on 2007-03-28
both computers are on ext3

the server is using software raid + lvm, if that happens to be pertinent

thanks
Kris

---

### Post by yagiska on 2007-03-28
Just an update:

The same thing happens on my other laptop, so it whatever the problem, it's not isolated to my one machine. The fact that they work fine on my server, and can be opened with GIMP on any machine, leads me to believe that the files are not corrupted.

Also, the fact that GIMP loads and that a local copy of the server JPG exhibits the same behavior leads me to believe it is not a problem with my NFS setup.

Any help is greatly appreciated.

Thanks!
Kris

---

