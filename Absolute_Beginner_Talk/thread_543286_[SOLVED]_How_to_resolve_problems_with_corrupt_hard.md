---
title: "[SOLVED] How to resolve problems with corrupt hard drive"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by stone on 2007-09-04
Last week I tried to start up my computer and it informed me that my Ubuntu partition was corrupt. So I ran fsck and cleaned it up. I then took all my important files (about 200 photos) and copied them onto a brand new hard drive formatted to ext3. Now when I boot it tells me that my new hard drive is corrupt and that I need to run fsck on it. What is this all about? I guess I can run fsck on it, but I'd like to find out what is causing all these problems. Do I have a virus? Is there a way I can identify what file is in trouble? Anyone have any ideas or suggestions?

---

### Post by nowshining on 2007-09-05
very few viruses are suppose to work on linux but it's very tough it requires you inputting a password to allow it to intall and junk..

fsck will run every 20 reboots/startups to do a check and that's normal - unless it is turned off...

:)

---

### Post by K.Mandla on 2007-09-05
Just curious, but are the file names unusual? Do they, for example, include letters from different character sets?

I ask that because I copied some files from a Windows machine that included filenames with a Japanese character set, and it sometimes caused me grief. Nothing major, but unusual it was.

Now like Yoda I will stop talking.

---

### Post by stone on 2007-09-05
Thanks for the responses. Unfortunately (I guess) the files are pretty regular. Just some pictures from my digital camera with no particularly strange names (they get imported as DCF001.jpg, DCF002.jpg, etc.)

---

### Post by nowshining on 2007-09-05
is that still a problem for u..

---

### Post by stone on 2007-09-07
Ok, so I did some research. This may be useful to other noobs like me.

I read the fsck log at: /var/log/fsck/checkfs

This told me that inode 11419650 had illegal blocks. Weird.

I used this command to find what that inode was pointing to:

```
find -inum 11419650
```

It was a digital photo, and not one that I particularly cared about anyway. I opened the photo and it seemed fine. If I remember my OS class a few years ago, what fsck was telling me is not that the photo was corrupt, but rather the inode that points to the photo.

I ran fsck and all is right with the world. I still don't know what caused the corruption but I'm guessing it was due to some crash or something (I know you guys won't believe this, but my Ubuntu machine does crash from time to time).

Hope this is helpful to someone else.

---

### Post by nowshining on 2007-09-08
great :) i'm glad u got it fixed..that post and how u solved it helped me learn something I can pass on to others..

---

### Post by az on 2007-09-08
> **stone said:**
>  I'm guessing it was due to some crash or something (I know you guys won't believe this, but my Ubuntu machine does crash from time to time).


I wonder why it is crashing for you.  And since this problem happened on two different drives, I suggest you have hardware problems.  It may be bad ram (run a memtest) or insufficient cooling (are your fans still working well).  There are endless other culprits, but those may be more likely.

You can run memtest overnight one night and then cpuburn for a few hours after that.  That should shake things down a little.  You can write a little script which will copy an iso image from one drive to the other ten times and then check the md5sum...

---

