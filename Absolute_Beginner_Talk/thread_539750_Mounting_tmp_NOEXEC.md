---
title: "Mounting /tmp NOEXEC"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by stjoenewt on 2007-08-31
I recently installed UBUNTU on my new PC.  I decided to create a separate partition for /tmp and mount it NOEXEC for security purposes.  I made the entry in FSTAB, however I still seem to be able to copy and run executables to the directory.  My entry is as follows,

# /dev/sda9
UUID=ccd7b545-c656-47a2-9c72-cee0a81b86c9 /tmp            ext2    nosuid,noexec   0       2

How can I prove that /tmp is in fact NOEXEC?

---

### Post by bogolisk on 2007-08-31
> **stjoenewt said:**
> I recently installed UBUNTU on my new PC.  I decided to create a separate partition for /tmp and mount it NOEXEC for security purposes.  I made the entry in FSTAB, however I still seem to be able to copy and run executables to the directory.  My entry is as follows,

# /dev/sda9
UUID=ccd7b545-c656-47a2-9c72-cee0a81b86c9 /tmp            ext2    nosuid,noexec   0       2

How can I prove that /tmp is in fact NOEXEC?

copy a executable file to /tmp and try to run it from there.
```

$ cp /bin/true /tmp/
$ /tmp/true

```

---

### Post by stjoenewt on 2007-08-31
Thanks for the quick reply BOGOLISK.  I copied the program you suggested and then tried to execute it using the command line you showed me.  I received the message "permission denied", which I assume means that I have successfully set /tmp to NOEXEC.   :)

Thanks again.

---

