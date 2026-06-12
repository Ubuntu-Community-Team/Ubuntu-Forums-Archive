---
title: "Dapper installation troubles, please read!"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by rkrug on 2006-10-07
Okay, so I'm trying to install Ubuntu 6.06 (Dapper Drake) and my CD boots up fine. I select install and it boots the kernel, I believe, but then when it begins to 'mount the root file system' it stops and a black screen comes up, like a DOS command line thing. It has a page of


[481.424391] buffer I/O error on device hdc, logical block 6

(with varying numbers each line)

and then when it's done displaying those this comes up:


Busybox v1.01 (Debian 1:1.01 -4ubuntu3) built in shell (ash)

/bin/sh: can't access tty; job control turned off
#
#


Any idea what's going on and/or how to fix this? If neccessary I will post my computers hardware, etc.

I have tried burning multiple CDs, at 16x 4x and 1x.

Help?

---

### Post by aldegaz on 2006-10-07
Are you burning the same .iso image again and again? It might be the .iso file you downloaded is corrupted.

You shouldnt have any problems.

Try downloading the .iso file again and burn it.

---

### Post by rkrug on 2006-10-07
I downloaded it from the Ubuntu site so I assumed it would be OK, but I'll try downloading again.

---

### Post by aldegaz on 2006-10-07
This is a very good example how to do a checksum even if your download comes from the ubuntu page:

>    1. Once you've downloaded Ubuntu, go to the bottom of the page that you downloaded from and click on a link that says "MD5SUMS".
   2. Then, in another window, download digestIT, an application for Windows that lets you verify the MD5 Checksums of files.
   3. Once you've downloaded and installed digestIT, use your Explorer window to go to the ISO file you downloaded.
   4. Right-click on the file, go to the digestIT menu, click "Verify MD5 Hash".
   5. Copy over the appropriate MD5 string (that you found during point #1, above).
   6. Verify.

---

### Post by rkrug on 2006-10-07
"Verification failed. Digest does not match."

---

### Post by rkrug on 2006-10-07
> **rkrug said:**
> "Verification failed. Digest does not match."

So what does this mean? There's something wrong with the file?

---

### Post by Darklighter137 on 2006-10-07
I'v never had that happen before, but it would indeed seem that the  ISO is bad.  Download a fresh one and try again. ^_^

---

### Post by arkangel on 2006-10-07
download it again , you have a stream of bytes comming one could be missing in the way from the ubuntu server to your computer

---

### Post by rkrug on 2006-10-07
Thanks for the help, I'm downloading Ubuntu from another server and the alternate version as well.

I will post here again once I try the new ISOs, and let you know how it turns out.

---

### Post by Frak on 2006-10-07
Did you burn it as an ISO image or an ISO file,
IT needs to be an Image!

---

### Post by rkrug on 2006-10-07
> **Frak said:**
> Did you burn it as an ISO image or an ISO file,
IT needs to be an Image!

It's an ISO image, booting fine. The problem is during installation.

---

### Post by Frak on 2006-10-07
Sorry

---

### Post by rkrug on 2006-10-07
The new ISO didn't work. I'll try the alternate install next.

---

### Post by rkrug on 2006-10-07
Okay, I'm trying the alternate install (the text one), but once it gets to the 'mount CD' part it says that it can't and that it might not be in the drive.

Any ideas? I've tried the 'irqpoll' command, but it only made it go a little further (although I don't even know what the command means/does)

Help? I'm desperate!

---

### Post by rkrug on 2007-02-21
well, now, a year later, now that I've installed Ubuntu successfully I can tell you all what my problem was:

The CD drive.

It was too old or slow or something.

---

