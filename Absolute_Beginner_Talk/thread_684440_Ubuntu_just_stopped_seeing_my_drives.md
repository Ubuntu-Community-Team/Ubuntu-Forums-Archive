---
title: "Ubuntu just stopped seeing my drives"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by ladybumavere on 2008-02-01
I dunno what happened but it used to automount all my drives and now it no longer sees any of them but the filesystem one.

Any help?

---

### Post by kpkeerthi on 2008-02-01
Do you mean.. ubuntu boots and mounts root filesystem but not the other ones? What happens when you type **sudo mount -a** in a terminal?

---

### Post by ladybumavere on 2008-02-01
> **kpkeerthi said:**
> Do you mean.. ubuntu boots and mounts root filesystem but not the other ones? What happens when you type **sudo mount -a** in a terminal?

Well here's the thing.  Usually they're visible through "computer" but they aren't any longer.  It only recognizes "File System" "DVD-RW" and "Floppy."

I dunno where the other drives went.

---

### Post by erginemr on 2008-02-01
Please post the outputs of the following commands from the terminal:
```
cat /etc/fstab
blkid
sudo fdisk -l
```
and give us more verbal info how many and what type of drives (fat, ntfs, etx3) you have, if you are dual-booting with Windows or not, etc.

---

### Post by kpkeerthi on 2008-02-01
OK. Did you try that command? It should print out some message about the problem and post that here so I can take a look at.
```
sudo mount -a
```

---

### Post by oedha on 2008-02-01
wait....did you shutdown your winblows correctly
that will happen after you put sleep on winblows then you jump to linux.....

~E~

---

### Post by ladybumavere on 2008-02-01
> **oedha said:**
> wait....did you shutdown your winblows correctly
that will happen after you put sleep on winblows then you jump to linux.....

~E~

Well that must've been the problem because yes in fact my windows crashed and then since then Ubuntu didn't see the drives.

However, I just booted back into Ubuntu to run those commands and now they're back and everything appears fine.


Thank you.

---

