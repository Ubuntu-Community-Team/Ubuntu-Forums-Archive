---
title: "Kernel Panic - not syncing"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by jebbench on 2007-12-28
Hey, I have a slight problem.

I was using my laptop (Compaq Presario 2500) yesterday and everything was working fine, I turned it on this morning and was greeted with the message:

```
Kernel Panic - not syncing : Attempted to kill init!
```

I have no previous kernels to boot into as it was a fresh install at Ubuntu 7.10 and the recovery mode dies at the same point:

```
[32.807597] Freeing unused kernel memory: 364k freed
Loading, please wait...
[32.827069] Kernel Panic - not syncing : Attempted to kill init!
```

Any ideas how i can get it up and running again?

Thanks
James Bench

---

### Post by blueridgedog on 2007-12-28
This means that the kernel encountered an error (prior to the msg), that it is not going to attempt to sync the file system and the error was that the number one process, init, attempted to die.

To debug this further, you will need to look further up the boot message screen for the error that preceded this.  Are there other messages on the screen when you get this one?

I have seen this in the past with hardware failures.  I would be curious to know if you could boot successfully off of the Ubuntu CD.

---

### Post by jebbench on 2007-12-28
Thanks for replying, I can boot with the Live CD no problems. There don't appear to be any errors in the start up, but i don't really know what I'm looking for.

---

### Post by jebbench on 2007-12-30
I've now reinstalled Ubuntu from the Live Disc and everything seems to be working fine.

---

### Post by blueridgedog on 2007-12-30
Excellent.

---

### Post by rmdegennaro on 2007-12-30
I just installed 7.10 server edition, and am receiving the same thing.  Well, not just.  I updated it and then put ubuntu-desktop on it because the client isn't so command-line orientated.  

The problem wound up being because the machine has a (rather old) built-in Fast-Trak Lite IDE RAID controller.  A colleague made RAID sets after the install and before the update.  I removed them and it booted fine.  

Strange that the boot-up before the update did not mind the raid set, but after the updates it did.  A new kernel?  Didn't notice.  Anyways, now to add the other drives with LVM.

Thanks for good forums Ubuntu!  Almost as good as Gentoo's.  :-)

---

