---
title: "[SOLVED] Vista &amp;amp; Ubuntu Home Folder in one?"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by skyhook19 on 2008-01-10
I was planning on dual booting Vista and Ubuntu together.  What I want is to have the home folder in Ubuntu the same as Vistas home folder.

I was thinking I could have three partitions one for Ubuntu one for vista and one for the home folder.  During Ubuntu setup I would set the home folder to the correct partition in ntfs.  (I'm fairly certain this parts okay)  Then In Vista I would change the location of the home folder to the Ubuntu one.  Any thoughts anyone?

Thanks!

Note:  I've been using Ubuntu for about a year now (dual booting with xp), and previously Ive had a separate share partition, but that's not near as good for me, I really like having the documents folder and stuff in the start menu, and I'd like the home folder in ubuntu to be available in windows.

---

### Post by PeterJS on 2008-01-10
This would be a VERY bad idea. NTFS doesn't support the file permissions necessary to make your home directory secure and workable. The settings are stored in in such radically different ways that their would be no benefit to having them in one place.

Consolidating documents in to one place is much easier though. Just make the NTFS drive larger rather an have a shared parition. Set up your account on windows first. And then when you set up your ubuntu account, Gnome will auto create ~/Documents,  ~/Pictures, and ~/Music folders, etc, before you put anything in those folders, delete them and then symlink them to their windows counter parts.

---

### Post by skyhook19 on 2008-01-10
Okay, so that sounds fantastic, but I don't know what you mean when you say symlink them.  Could you explain?  and is it bad that I don't know what that means by now? :)

---

### Post by PeterJS on 2008-01-10
Symlinks are a special kind of file that is a lot like windows shortcuts only more power bucause instead of just pointing to the files or folders, they can actually be used interchangeably with the file they point to. So if you symlink ~/Documents to /media/windows/Documents\ And\ Settings/user/My\ Documents/ the two folder names would both point to the same part of your NTFS parition.
To set up a symlink:
```

ln -s /thing/you/want/to/link/to /home/user/where/you/want/the/link/

```

---

### Post by skyhook19 on 2008-01-13
This worked excellently, thanks a bunch!

---

