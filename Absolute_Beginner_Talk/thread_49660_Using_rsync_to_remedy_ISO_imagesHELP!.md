---
title: "Using rsync to remedy ISO images?HELP!"
date: 2005-07-17
forum: Absolute Beginner Talk
---

### Post by coolblue on 2005-07-17
What is rsync? I have the ISO image of a distro which does not match the md5sum. Someone told me it that the image can be remedied by using rsync.

What is this rsync and how do I use it to fix my ISO image?

Plz help the newbie!

Thanks

---

### Post by dave9191 on 2005-07-17
Rsync (remote synchronisation) is an inteligent version of rcp (remote copy) which copies files from one location to another (possibly another computer). Great for making backups. Rsync only copies the differences between files (unlike rcp which copies everyhing), hence it speeds up the process. I have another computer to which I rsync my home directory with as a backup. 

As for iso images, I heard that some people update their iso images using rsync to minimise bandwidth ([http://lists.tinysofa.org/pipermail/tinysofa-discuss/2004-May/000074.html)](http://lists.tinysofa.org/pipermail/tinysofa-discuss/2004-May/000074.html)). Because the md5 check sum doesnt match, it meand that you have a bad download of the iso image. You can try to use rsync to update your iso with one from a download site, or you could just download the whole iso image again. 

Dave

---

### Post by coolblue on 2005-07-18
Can u plz give details on how to do this?
I'm a TOTAL newbie. Pleeeeeeeeez give sufficient details & clear explanations.

Thanks a lot.

---

### Post by dave9191 on 2005-07-18
I found you this nice link, which is clearer then the previous one. [http://www.mirrorservice.org/help/rsync.html](http://www.mirrorservice.org/help/rsync.html) 

To rsnc you need to know the location of the remote iso file and the server you are rsyncing from must support rsync.

Dave

---

