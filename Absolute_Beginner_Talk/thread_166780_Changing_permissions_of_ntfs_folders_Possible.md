---
title: "Changing permissions of ntfs folders? Possible?"
date: 2006-04-27
forum: Absolute Beginner Talk
---

### Post by thesm on 2006-04-27
New to Linux and Ubuntu and really liking it.  My main problem is that windows is on my main partition (ntfs) with all my data.  I'm planning move it all across to my shiny new ext2 formatted HDD sometime soon but all of this is by-the-by.  

My windows partition is mounting fine but I'd like to be able to change the permissions of some of the folders on there, just wondering if that's possible seeing as you can't write to ntfs.

---

### Post by frodon on 2006-04-27
NTFS and FAT32 file systems don't support unix rights and ownership therefore you can't change the rights on them.
The only thing you can do is to set the same rights for all the files in the partitions thanks to the mount command, it's just a kind of hack.

---

### Post by thesm on 2006-04-27
Ok, thanks for the quick reply.

---

### Post by Rinzwind on 2006-04-27
You can write to NTFS. The people claiming it's not possible are wrong. Since kernel 2.6.4 it's doable. 

BUT: **NTFS 'write' support for 2.6.4 is limited to overwriting or editing existing files while maintaining the same file size. You may not create files or folders or remove them.**

So changing permitions is something that can be done (it doesn't alter the files size in any way) but you are doing something extremly risky nevertheless. 

And now for some extra free (as in no charge) info about something very cool : [http://www.fs-driver.org/](http://www.fs-driver.org/)

Do it the other way around: store all your files on ext3 en let windows access those drives! And it brings you another BIG step towards letting go of the OS supporting DRM :evil:

---

### Post by thesm on 2006-04-27
Ok thanks, I don't think I'll worry about it then.  Also, thanks for the link, I'm actually using it at the moment and it's working really well.  I'm slowly making the change to ubuntu, it's only a matter of time now until windows is ditched except for occasional gaming.

---

### Post by Rinzwind on 2006-04-27
[QUOTE=thesm]Ok thanks, I don't think I'll worry about it then.  Also, thanks for the link, I'm actually using it at the moment and it's working really well.  I'm slowly making the change to ubuntu, it's only a matter of time now until windows is ditched except for occasional gaming.[/QUOTE]

No problem. I started this year with Ubuntu and am NEVER going back again. NEVER. Man, I hate my win machine at work (it'll be Ubuntu someday too!).
After a time with Breezy I can claim I am totally hooked on Dapper Drake O+ My best OS to day (and I had a few :P )

Oh and regarding gaming: get a PS1 (cheap) or PS2 (good games) if you really don't like MS. Or an XBox if you fancy the games for it.

---

