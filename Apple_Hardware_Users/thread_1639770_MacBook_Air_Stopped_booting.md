---
title: "MacBook Air: Stopped booting"
date: 2010-12-07
forum: Apple Hardware Users
---

### Post by eyerouge on 2010-12-07
I recently installed Ubuntu 10.10 (64) on my MacBook Air (3,2) and have followed all instructions in Wiki - it all worked out flawless. Yesternight, after updating the Kernel to 3.6.35-23-generic via Ubuntus own update & tinkering with fan settingsm it stopped booting at all. 

When using 3.6.35-23-generic from Grub2 (1.98) I get the following error and can't boot into my Ubunt: 
```

Modprobe: FATAL: Error inserting pad lock_sha (/lib/modules/2.6.35-23-generic/kernel/drivers/crypto/padlock-sha.ko): No such device.
```


Rest of error message below is in Swedish, and I've translated it freely:


```
”The disk for / is not ready yet or does not exist.

Continue to wait; or press S to skip mount or M for manual stuff.”
```


(If I press S once it says ””The disk for /temp is not ready yet or does not exist.”

When trying to boot with 2.6.35-22 I don't get any error messages at all, it just fails to boot and shows blank screen. When trying to enter using recovery mode and 2.6.35-23 (from Grub) it also halts when it comes to the following lines:

```
init: plymouth main process (71) killed by SEGV signal
Modprobe: FATAL: Error inserting pad lock_sha (/lib/modules/2.6.35-23-generic/kernel/drivers/crypto/padlock-sha.ko): No such device.
```


Anyone has an idea what's going on? I have been using Ubuntu for several years and never managed to burn the system, not to mention doing it within 24h of an install and latest updates.

---

### Post by eyerouge on 2010-12-27
This very same thing has happened once more: Yet again it was on a fully operational Ubuntu 10.10 (64) on the same machine - a MacBook Air 3,2.

This tie around I didn't update anything, so the Kernel track above is probably a bad one.. :)

Anyone have a clue what the error messages mean? Having two of these meltdowns within very short time makes it virtually impossible to keep Ubuntu on the machine since I can't even login as it is now.

---

### Post by tgalati4 on 2010-12-27
So you are not allowed or can't boot into your previous kernel?  It should still be on the disk.  That's precisely the reason that old kernels stick around.

---

### Post by eyerouge on 2010-12-27
> **tgalati4 said:**
> So you are not allowed or can't boot into your previous kernel?  It should still be on the disk.  That's precisely the reason that old kernels stick around.

Kernel is fine, and I am able to boot into non-graphical mode and am able to login in terminal mode only. It seems like the hd isn't properly mounted, but then again, if it isn't I wouldn't be able to boot at all.

---

### Post by tgalati4 on 2010-12-28
Well, the error messages are saying that the kernel is trying to load a cryptography module (perhaps a fingerprint reader or other hardware security device) and it can't find it.  So, put that module in the blacklist file and see if it boots or recompile the kernel without that crypto setting in the kernel configurator.

It's possible that the hard disk is mounted as read-only which would allow limited boot.  This is done as a protective measure when major breakage is encountered.  

cat /etc/fstab
cat /etc/mtab

---

