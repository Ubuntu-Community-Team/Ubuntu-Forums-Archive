---
title: "External HD works on Live session... what about system?"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by chang3andrew on 2008-02-21
Hey, I first installed Ubuntu and found out that I couldn't mount an NTFS external hard drive. But after I reinstalled windows, and ran Ubuntu on a live CD, I plugged my external hard drive and it worked, I could type on the documents and look at the pictures I stored in there.

So if I install Ubuntu, will I still be able to mount an NTFS hard drive? or will I have issues? I'm planning on reinstalling Ubuntu if I can.

---

### Post by Trail on 2008-02-21
I don't see any reasons why it shouldn't. Especially if it plays on live-cd.

---

### Post by chang3andrew on 2008-02-21
I don't know, maybe it's just the way that it was installed that made everything mess up. But what if I do install it and it won't accept NTFS?

---

### Post by FrozenFox on 2008-02-21
Gutsy (it works fine in Feisty and Hardy) has a few dumb issues with dealing with hard drives outside of what it's installed on. You can safely install assuming you -can- get it to work, but it's possible you might need to fix a couple things first, which is typically pretty easy and quick and can be done graphically, and if it doesn't work it's not very difficult to add the correct entry to fstab to fix it.

In short: go ahead and install. If you have problems, come back and see us, it should be a painless fix.

---

### Post by chang3andrew on 2008-02-21
oh...oh... OH THAT'S why....

I think I know why it didn't work the first time: The external hard drive was once a hard drive of a laptop that I eventually ceased to use... so I had windows operating system data still within its memory. No wonder it was telling me I had to stop the programs within the hard disk before I can mount it... AH.....

So, I'm wondering, with that taken care of... if I install ubuntu again, will my hard drive (which is actually formatted now) run? I'd like to say so... :)

---

### Post by FrozenFox on 2008-02-21
> **chang3andrew said:**
> oh...oh... OH THAT'S why....

I think I know why it didn't work the first time: The external hard drive was once a hard drive of a laptop that I eventually ceased to use... so I had windows operating system data still within its memory. No wonder it was telling me I had to stop the programs within the hard disk before I can mount it... AH.....

So, I'm wondering, with that taken care of... if I install ubuntu again, will my hard drive (which is actually formatted now) run? I'd like to say so... :)

Linux can read windows hard drive memory by default (module ntfs is included with it, and the ntfs-3g module for 'better' support is available in synaptic), that was not likely the issue. If you are considering installing Ubuntu Gutsy Gibbon, it just has some issues (whereas its predecessor, 7.04 aka Feisty and its successor 8.04 aka Hardy dont have the same issue) with mounting hard drives outside of the ones the os is installed on. As said before, it isn't too terribly difficult to fix though.

---

