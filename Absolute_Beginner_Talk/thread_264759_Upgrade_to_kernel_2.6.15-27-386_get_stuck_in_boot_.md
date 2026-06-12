---
title: "Upgrade to kernel 2.6.15-27-386 get stuck in boot process"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by nighthawk06 on 2006-09-25
Hi all,

I am a beginner with ubuntu..
I have succeeded with installing the basic 6.06 386 ubuntu os.
Yet, after adding the recommended updates, when I boot with the new kernel 2.6.15-27-386 it get stuck in Loading Hardware drivers.

How can I view a log or something like it to see where exactly it get stuck?

---
Thanks

---

### Post by wieman01 on 2006-09-25
All the necessary logfiles are here:
> /var/log
If you haven't disable the boot-log then there should be a file called "boot" or similar. Cannot validate this because I have disabled it.

---

### Post by nighthawk06 on 2006-09-25
> **wieman01 said:**
> All the necessary logfiles are here:

If you haven't disable the boot-log then there should be a file called "boot" or similar. Cannot validate this because I have disabled it.

on the /var/log dir I can find only /var/log/bootstrap.log and /var/log/btmp

Anyways, in the bootstrap.log I do not know how to located the exact problem, what should I look for in this file? (if it is the correct file)

---

### Post by nighthawk06 on 2006-09-25
I found a file named "dmesg" which displays information about the boot sequence.

Yet, unfortunatly, it contains only updated information about the 2.6.15-23-386 kernel which is the old kernel that I am using. I tried running the system with the new kernel until it get stuck again... and booted from the installation cd and viewed the file -- it still contained information about the old kernele boot sequence.

How can I in boot time view this log on the screen if it is possiable at all, that might give me an idea where the machine get stuck in the boot.

---

### Post by nighthawk06 on 2006-09-25
solved the issue...

The hard disks were wired wrong,.
The jumpers weren't set properly.

Found it and fixed it,. now ubuntu works properly.

---

