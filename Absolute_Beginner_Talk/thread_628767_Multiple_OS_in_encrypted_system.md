---
title: "Multiple OS in encrypted system"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by Niniel on 2007-12-01
Hello,

I installed Ubuntu on a computer of mine with disk encryption (and LVM). I am wondering now if it was possible to install another distribution on the encrypted LVM volume next to Ubuntu so that both are encrypted and can share the encrypted swap partition. 

Thanks.

---

### Post by Niniel on 2007-12-11
Anybody?
I wanted to test-drive Fluxbuntu, but I don't really feel like wiping my (encrypted) partition just for that.

Although I may be out of luck anyway, I don't think I left any free space on the partition, and I dimly recall reading something about not being able to resize the partition anymore after encrypting.

---

### Post by HermanAB on 2007-12-11
Yes, install VMware Server then install as many other systems as you want in virtual machines.  That is the only way I can think of that will work on an encrypted volume.

Cheers,

H.

---

### Post by Niniel on 2007-12-12
Ok, thanks.

So if I wanted to have 2 LVM encrypted OS on the same computer, I'd have to set up one encrypted drive for each of them? They should be able to share the boot partition though, right?

---

### Post by hyper_ch on 2007-12-12
yes, the can share the boot partition, with a fully encrypted system that's the only thing that still requires to be unpartitioned.

As different OSes handle the encryption differently I'd also setup just another disk (or partition) for a second OS and use its mechanisms for encryption. (I guess you could also use the same swap partition.)

---

### Post by Niniel on 2007-12-12
The same swap partition is inside the encrypted LVM volume, so that would be impossible to share unless I can find a way to get in there without launching Ubuntu, and then install something else (another Linux distribution) alongside it.

---

### Post by hyper_ch on 2007-12-12
there's a nice howto on howto encrypt a swap drive,... so you just need a partition for it....

[http://ubuntuforums.org/showthread.php?t=302167](http://ubuntuforums.org/showthread.php?t=302167)

Same works in feisty and gutsy...

---

