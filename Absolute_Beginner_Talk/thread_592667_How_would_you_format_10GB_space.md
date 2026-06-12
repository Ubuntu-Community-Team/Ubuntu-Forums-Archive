---
title: "How would you format 10GB space?"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by Enigman on 2007-10-26
I have a small 20GB HD in an older laptop.  The Windows partition is 10GB.  That leaves 10GB remaining for Ubuntu.  How would you partition this?
I have 512 ram.

My first pass on what to do is:
/home  4GB
/   4.2 GB
/swap  768MB

I honestly don't know if this is big enough for root.  This laptop is used for Word processing and web browsing only.  Plus I'm learning Linux on it!

Thank you for the help.

---

### Post by linyanam on 2007-10-26
Hi I have big hard drive so gave 20gb to / and 20gb to /home.
I install all sorts of stuff to try and then delete them. Currently my / partition is using 3.6gb.
So your settings seem right to me. But I am not expert. Some where I read 5GB for /, but I have laptop and desktop with Ubuntu and never needed 5 for / partition alone.
This is just my experience.
Cheers,

---

### Post by jualin on 2007-10-26
I think that root of 4.2 GB is good enough, now you probably are not going to be able to install that many programs. But if you want to use the computer for web browsing and Word processing that should be enough, Open Office does not take that much space so you should be good. Maybe I will reduce a little the home space and give about 5 GB to root and about 3 GB to home. 
In my own experience I have never needed more than 2 GB for the home folder, unless I save a lot of music and downloads to it.

---

### Post by linyanam on 2007-10-26
Plus follow the post which says how to clean your system,so that you can release space after all your tinkering. 
[http://ubuntuforums.org/showthread.php?t=140920&highlight=unnecessary](http://ubuntuforums.org/showthread.php?t=140920&highlight=unnecessary)

---

### Post by Enigman on 2007-10-26
Thank you to all who have replied so quickly.  I will make these changes and follow the clean up link.  Thank you.

---

### Post by Twintop on 2007-10-26
I'd set it up like this:

1GB  - Swap
100MB - /boot
4GB - /
3.9GB - /home

So you have more swap space to work with, and /boot is self contained. You might be able to shrink /boot down to 50-75MB if you want, but if a Kernel upgrade comes out, you might have some problems. :)


EDIT: Oops, looks like I missed you. Let us know how it turns out!

---

### Post by az on 2007-10-26
> **Enigman said:**
> I have a small 20GB HD in an older laptop.  The Windows partition is 10GB.  That leaves 10GB remaining for Ubuntu.  How would you partition this?
I have 512 ram.

My first pass on what to do is:
/home  4GB
/   4.2 GB
/swap  768MB

I honestly don't know if this is big enough for root.  This laptop is used for Word processing and web browsing only.  Plus I'm learning Linux on it!

Thank you for the help.

I would forget about the separate home altogether.  There are better and safer ways of backing up your data anyway.  Easier, too.  

That way, you don't run the very real risk of running out of space somewhere.

---

### Post by sneezymelon on 2007-10-26
I agree with jualin.
2GB for home should be good

---

