---
title: "what does unmount drive do?"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by Likenota on 2007-07-22
okay my desktop on ubuntu has my hard drives when i right click them i see umount drive what does this do exactly' ?  i have an ntfs drive on there with windows partition and im tryin to get it to read in vmware.. (sata)  so im wondering what this unmount means..

---

### Post by wolfen69 on 2007-07-22
unmount means it will no longer be "connected" to your computer. you will not be able to access it.

---

### Post by Likenota on 2007-07-22
why would u wanna do that.. thats stupid.

---

### Post by Pom2122 on 2007-07-22
> why would u wanna do that.. thats stupid.

It  isn't stupid. Suppose you want to run a disk maintenance program (fsck, etc) on a drive? Linux won't normally allow you to do it with the drive accessible and in a writable state.

BTW the command line command is umount, not unmount. 
:)

---

### Post by HermanAB on 2007-07-22
In Windoze, the equivalent is the 'net map' command.  It ties a storage device to a drive letter.  The unmount is handled by little kludges like: "Safely remove your USB device" in the "System Tray".

Cheers,

Herman

---

### Post by Likenota on 2007-07-22
so is that what i need to do to make it be read by vMware? is too unmount it ?

---

