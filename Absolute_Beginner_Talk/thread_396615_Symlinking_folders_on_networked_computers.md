---
title: "Symlinking folders on networked computers"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by brennydoogles on 2007-03-29
I have a network in my house with three computers and an NDAS network Hard drive for extra storage. Because the drive requires proprietary software to be run as a network drive, I can't access it through ubuntu on this computer. Not a problem, I just shared it on oneof the computers with read/write access and everything is ok. I can access the drive through the networking gui, but it's like 15 clicks for something that I use pretty often. My question is, how would I create a symlink on my desktop to that particular "folder"??

---

### Post by bignickel on 2007-03-30
Is the drive listed in /mnt or /media anywhere?  You can make a symlink by opening a terminal and typing

```
ln -s /mnt/mydrive mydrive
```

Where /mnt/mydrive is the location of the network drive.  This will put a new link in your current directory called mydrive.  Does that answer the question?

---

### Post by brennydoogles on 2007-03-30
> **bignickel said:**
> Is the drive listed in /mnt or /media anywhere?  You can make a symlink by opening a terminal and typing

```
ln -s /mnt/mydrive mydrive
```

Where /mnt/mydrive is the location of the network drive.  This will put a new link in your current directory called mydrive.  Does that answer the question?

It does make sense, and I am fairly familiar with Symlinking, but because the folder resides on a completely separate computer (my wife's computer, which is on the same router) I don't know how to do it. The drive does not show up in /mnt or /media .

---

### Post by bignickel on 2007-04-02
So before you even think about symlinking you have to make sure they're mounted properly.  I'm not quite clear on how they're accessed.  Are they in the fstab anywhere?

---

### Post by brennydoogles on 2007-04-03
> **bignickel said:**
> So before you even think about symlinking you have to make sure they're mounted properly.  I'm not quite clear on how they're accessed.  Are they in the fstab anywhere?

No. It is actually a network harddrive, which is mounted on another computer, which was then shared, and I now access by means of my windows network. Could I make it any more confusing??

---

