---
title: "Second hard drive mounts but doesn't appear in 'Places'"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by guyweb on 2006-08-25
I have successfully installed a new storage hard drive. 

I formatted in ext3 format and created a single partition using the gparted app. I created a mount in /media/ and I then used nautillus to edit the fstab file so that the computer would find it on startup.

I can read and write to it no problem.

My problem is that the drive does not appear in 'Places'. It appears no probs in Places/Computer but not in 'Places'.

I have an external USB drive that appears in 'Places'. I'd like my internal HD to appear there too..

The reason being that unitl it does appear there i cannot directly save anything to it. For example, in open office i cannot save a document to my internal drive becuase i cannot navigate to it within the 'save as' panel.

Any ideas how i might get it to appear in 'Places'?

Many thanks,

Guy.

---

### Post by Spookster on 2006-08-25
In nautilus, browse to the hard drive and then click Bookmarks -> Add Bookmark (Ctrl-D) - this will make it appear in Places.

(It adds the folder to .gtk-bookmarks in your home directory).

---

### Post by TooDamFast on 2006-08-25
i have a questions on the same grounds.  (i added the bookmarks, their great!)  but

my hard drives dont show up under "computer"

their mounted (i can access them from the bookmarks!) and i can read and write to them but they dont show up with the other drives.  any way to add them?

---

### Post by djsroknrol on 2006-08-25
Another way might be through the Configuration Editor...

Applications>System Tools>Configuration Editor

Drill down to Apps>Nautilus> and check the ones you need there...

---

### Post by guyweb on 2006-08-26
Thanks Spookster, that worked a treat. It's now appeared in the places menu and all is great!

---

### Post by etaham on 2007-02-09
I'm having the same problem after repartitioning 2 hard drives.  Neither of them are showing up in places, although they are mounted in /media and are working properly.  I don't have any hard drive type entries under apps>nautilus.  Any ideas?

---

### Post by clayg on 2007-07-21
same problem here - what ever happened to using the /mnt directory for mounted hard drives?

---

