---
title: "Locked folders in HFS+ partition"
date: 2007-07-07
forum: Apple Intel Users
---

### Post by ripdog on 2007-07-07
Hi,

In Feisty I mounted my HFS+ partition for the purpose of getting at my iTunes music. However, in my Users/Ripdog folder, a few folders give me access denied errors when I try to access them. One of which is the Music folder, under which is iTunes music. 

The locked folders appear to be the ones by default on the finder's sidebar like Music, Pictures, Movies... 
All user created folders are accessible.

Anyone got any ideas?

---

### Post by cosborn72 on 2007-07-07
Have you tried changing the permissions in OSX?  Open you home folder, right click on the music folder and go down to ownership and permissions.  OSX should allow you to modify the permissions.  I suspect you would have to set "Others" access to read and write.

I would probably change it back once you have transferred the music, but that's just me.  I haven't tried this yet, so I can't promise it will work, but I vaugly remember having to do this at one point in the past.

---

### Post by cyberdork33 on 2007-07-07
> **cosborn72 said:**
> Have you tried changing the permissions in OSX?  Open you home folder, right click on the music folder and go down to ownership and permissions.  OSX should allow you to modify the permissions.  I suspect you would have to set "Others" access to read and write.

Yep. OSX uses file permissions just like linux. This means that those folders are marked as being owned by some other user and you do not have access. Set the "others" permissions to read only if you want to access the files inside.

---

### Post by ripdog on 2007-07-07
Thanks! Ill try that...

EDIT: It worked! Thanks.

---

