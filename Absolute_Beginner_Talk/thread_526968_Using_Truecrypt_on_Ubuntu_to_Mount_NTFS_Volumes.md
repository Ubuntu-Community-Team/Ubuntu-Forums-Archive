---
title: "Using Truecrypt on Ubuntu to Mount NTFS Volumes"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by kingleer on 2007-08-16
Hello, 

   I've been using Ubuntu for a couple of months now. I'm getting ready to leave windows all together, but I still don't know to use Truecrypt with Ubuntu. 

I've installed truecrypt on Ubuntu 7.04 no problem. I also installed a linux gui for truecrypt called forcefield 

[http://www.bockcay.de/forcefield](http://www.bockcay.de/forcefield)

and still have had no luck. 

MY PROBLEM: I have an encrypted Truecrypt Partition formatted with the NTFS file system, and I don't know to mount it. I can't even find the path of the volume in order to mount the freaking thing. Actually, I can't find a terminal command to list all the HDDs/partitions on my comp. 

Little help / links?

---

### Post by ppietryga on 2007-08-16
I don't have any Truecrypt experience, bu to list all your partitions type:
```

sudo fdisk -l

```
in terminal.

---

### Post by kingleer on 2007-08-16
Yes, thanks. 

I was able to mount the volume in the directory /mnt/tc.  But now I can't access the folder. 

I get an error that says - 

The Folder Contents Could not be Displayed

You do not have the permissions necessary to view the contents of "tc."

I posted a pic of the error message. Any idea on how to fix this?

---

### Post by kingleer on 2007-08-16
Oops.

Disregard that last post. I just mounted the volume using the terminal in root. Problem solved.

Except, I can't write files to the volume, but I can see its contents. I get the error - 

Error - 

Error while copying to "/mnt."

You do not have permissions to write to this folder. 

Error - 

Any Idea how to solve this problem.

Thankyou for your help ppietryga.

---

