---
title: "power failure now get error when booting"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by richardspirit on 2007-08-06
Recently I had a power failure and now I can't get Feisty to reboot. I keep getting this error

The Program 'apt-get' is not installed. 

I tried pressing Control-D but shell would not boot either.

Is there a way that I can try and fix the installation without losing data?

---

### Post by Jimmyfj on 2007-08-06
I recently had the same issue with my server - And the only way I was able to save the data on the servers disk was through a live cd. After recovering the data needed I simply re-installed the system.

---

### Post by milosz.galazka on 2007-08-06
At first you should boot in single user mode (or from live cd) and run *fsck* (only) over your linux partitions. How to enter single user mode is [here]("http://lists.slug.org.za/pipermail/slug-tech/2005-May/001219.html").

Then go [here]("http://ubuntuforums.org/showthread.php?t=457096") (just first part)

PS. OK, you probably can ommit first step

---

### Post by richardspirit on 2007-08-06
> **milosz.galazka said:**
> At first you should boot in single user mode (or from live cd) and run *fsck* (only) over your linux partitions. How to enter single user mode is [here]("http://lists.slug.org.za/pipermail/slug-tech/2005-May/001219.html").

Then go [here]("http://ubuntuforums.org/showthread.php?t=457096") (just first part)

PS. OK, you probably can ommit first step

Thank you so much. Everything is working perfectly again.

---

