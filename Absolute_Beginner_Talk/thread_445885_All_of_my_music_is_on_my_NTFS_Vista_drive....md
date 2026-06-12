---
title: "All of my music is on my NTFS Vista drive..."
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by gohanssjn on 2007-05-16
Is it save to use 3g to access it?  I won't really be writing to the drive, just reading mp3's and .m4a's.  Do I even need 3g to do this, or is reading NTFS fine in Ubuntu?

Of course, I won't really be using a rating system for my songs, but maybe Rthythm box might try to write play counts to the drive...or is that kept local on the ext3 partition I have?

---

### Post by taurus on 2007-05-16
NTFS driver is fine if you only want to read from ntfs filesystem.

---

### Post by Terl on 2007-05-16
> **gohanssjn said:**
> Is it save to use 3g to access it?  I won't really be writing to the drive, just reading mp3's and .m4a's.  Do I even need 3g to do this, or is reading NTFS fine in Ubuntu?

Of course, I won't really be using a rating system for my songs, but maybe Rthythm box might try to write play counts to the drive...or is that kept local on the ext3 partition I have?


I use ntfs3g to do this myself.  I got it through synaptic along with the configuration tool which makes the setup a snap.  You can set it up with the tool for read and write access.  I have not had issues but it is said not to be perfect.

---

### Post by starcraft.man on 2007-05-16
You don't need the 3g drivers just to read, I copy things off my XP drive(ntfs) sometimes and it works fine. The 3g drivers are really only for writing... if your not doing that don't bother getting them. I would recommend however if your data isn't too huge that you copy it to your home partition, you never know when you may want to change the tags or some other such task involving writing.

As for the rhythmbox question, not sure... I think it has its own local files.

That should be it for your question :)

Edit: rats again, *stares at taurus*

---

### Post by gohanssjn on 2007-05-16
Excellent, thanks.  Didn't want to make a partition for just my music like I've had in the past.

---

### Post by taurus on 2007-05-16
> **starcraft.man said:**
> 
Edit: rats again, *stares at taurus*

#-o

---

