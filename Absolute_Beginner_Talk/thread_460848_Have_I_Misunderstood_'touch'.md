---
title: "Have I Misunderstood 'touch'"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by Catsworth on 2007-06-01
Hi Guys,

I've just been looking at the 'touch' command, which (if I've understood it correctly) either:

a) if the specified file exists, update the *Accessed* and *Modified* times to the current date and time, or
b) create the specified file with a size of 0

So, assuming the file exists, the following should work ok:

```

touch /home/catsworth/myFiles/touchFile.txt

```

However, if I check the *Accessed* and *Modified* dates before and after they remain the same.  I can only get them to change by actually editing the file.

I tried using:

```

sudo touch /home/catsworth/myFiles/touchFile.txt

```

Just in case it was a permissions thing, but that didn't work.  I've also tried adding the -a switch to explicitly tell it to modify the *Accessed* date/time but that doesn't help either.

Have I misunderstood, or am I missing something here?

Thanks.

---

### Post by Catsworth on 2007-06-01
I think I solved it.

I was trying to 'touch' a file on a FAT32 file system, I take it that 'touch' doesn't work on FAT32?

---

### Post by hachuah on 2007-06-01
No, that is the correct usage of touch. How are you checking the access/modified times? Using ls -l ? The other thing to check is whether the disk is mounting read only... check at /etc/fstab.

---

### Post by Jussi Kukkonen on 2007-06-01
FAT saves very limited metadata on files, I believe modify/access times are not among that data.

---

### Post by Catsworth on 2007-06-01
That's what I figured, thanks guys :)

---

