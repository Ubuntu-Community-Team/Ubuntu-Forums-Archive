---
title: "How to format a hard drive I don't have access to"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by holdie on 2008-03-23
We've been using an external drive (MyBook 500GB)  to backup our apple computer, and recently it started acting buggy and now isn't being recognized by the OS...

Basically, it started telling us that it was "read only" before failing to be recognized at all

I hooked it up to my ubuntu computer and it was recognized fine, but obviously I didn't have access to write to the drive (I checked the permissions and it says the owner is "99")

What I'd like to do is format the drive and start over, perhaps the apple OS bugged out and changed the permissions but hopefully a format will work

any ideas?

---

### Post by kdarkentity on 2008-03-23
So basically when you use it on linux the hard drive mounts and you can read it, but you aren't allowed to write to it?

---

### Post by pHreaksYcle on 2008-03-23
I hope for your sake I am wrong but I believe your hard drive is dead. I got a similar message on a laptop driver about being read only and it was found to be dead as a doornail. Once again, I hope I'm wrong and good luck!

---

### Post by smoker on 2008-03-23
i believe the 'gparted' livecd will allow you to format the drive, you could also try the command:

sudo chown -R user:user /mount point of drive/

(going from memory with above command!)

gparted here: [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by herbster on 2008-03-23
Run Gparted, if not installed open a terminal and do

```
sudo apt-get install gparted
```

Then System > Admin > Gparted and in the upper right select the drive, unmount if it's mounted and hit Delete, then click on the space, New, set the filesystem (ext3, fat, etc.) and Apply.

---

