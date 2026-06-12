---
title: "can't write to hfs+"
date: 2005-07-16
forum: Apple PPC Users
---

### Post by philipscard on 2005-07-16
I cannot make the hfs+ partition of my drive writeable from linux (it mounts and reads fine), as either user or root, in terminal or Konqueror.
Its fstab entry is:

/dev/hda7   /mac     hfsplus rw,auto,users,exec    0   0

According to hours of websearching, this should, by rights, work...

[running a dual boot kubuntu/os8.6 lombard powerbook]

---

### Post by audiorevolution on 2005-07-17
Maybe you simply don't have the permissions?  I have my Pismo set to dual-boot OSX (for photography work) and Ubuntu (for everything else), and I keel all of my files on a partition between the two others.  I have the permissions set for all users on my files partition (chmod -R a+rw /whatever/directory/here), and the problem of permissions is a problem no more.  I would suggest this if it is a permissions issue.

---

### Post by philipscard on 2005-07-17
solved! Thank you for the suggestion - mac classic to linux is proving a very steep learning curve. Rather than open the partition to all users, I changed the owner of important directories from root to my main ID, and can now write to it (though bizarrely, when it was root, I couldn't write to it as root... Best not worry about that!).

---

