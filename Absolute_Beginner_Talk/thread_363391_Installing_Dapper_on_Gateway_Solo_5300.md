---
title: "Installing Dapper on Gateway Solo 5300"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by scottvan on 2007-02-16
Hello, this is my first post.  I am having problems installing Dapper on my 5300 with a 600mhz Celeron and 384mb memory.  After a few minutes of installing, all I get is a flashing cursor in the upper left hand corner and no further activity.  I have tried installing Xubuntu also, and I get the same result.  The laptop runs Win98 with no problem, so I don't think I have a hardware problem, I just don't know what is wrong.  I have successfully installed Dapper on a Compaq laptop.  Anyone have any ideas?

---

### Post by sy278 on 2007-02-17
> **scottvan said:**
> Hello, this is my first post.  I am having problems installing Dapper on my 5300 with a 600mhz Celeron and 384mb memory.  After a few minutes of installing, all I get is a flashing cursor in the upper left hand corner and no further activity.  I have tried installing Xubuntu also, and I get the same result.  The laptop runs Win98 with no problem, so I don't think I have a hardware problem, I just don't know what is wrong.  I have successfully installed Dapper on a Compaq laptop.  Anyone have any ideas?

I suspect its being caused by the ATI Graphics system, I'm not sure how to resolve it but I know there is a fix, I believe you need to alternative install CD.


Can anyone shed more light?

---

### Post by scottvan on 2007-02-17
What is the alternative install CD?

---

### Post by Maestro23 on 2007-02-17
> **scottvan said:**
> What is the alternative install CD?

[http://mirror.cc.columbia.edu/pub/linux/ubuntu/releases/edgy/](http://mirror.cc.columbia.edu/pub/linux/ubuntu/releases/edgy/)

Don't know your geographical location, you can pick a mirror closer to where you are in the Downloads section.  Just did this link to show you.

Good luck.

---

### Post by scottvan on 2007-02-17
Thanks!  I will try that when I get home.

---

### Post by scottvan on 2007-02-17
Ok, I tried the alternative install CD, but I get an error message saying that my computer does not have enough memory, and needs 36MB minimum.  My BIOS is reporting 384MB.  I ran Memtest from the CD, and it says I only have 32MB.  Can anyone help with this?

---

### Post by scottvan on 2007-02-21
Well, as is usually the case with me, Operator Error.  I pulled out the memory chip from the computer and it actually was only 32MB!  I was reading it wrong from the BIOS screen, partly because I only had a 1/2 second to read it when it displayed.  So I will get more memory and that should hopefully fix the problem.

---

### Post by scottvan on 2007-03-17
> **Maestro23 said:**
> [http://mirror.cc.columbia.edu/pub/linux/ubuntu/releases/edgy/](http://mirror.cc.columbia.edu/pub/linux/ubuntu/releases/edgy/)

Don't know your geographical location, you can pick a mirror closer to where you are in the Downloads section.  Just did this link to show you.

Good luck.
Just an update on my ancient laptop project... It works!  I had to replace the existing memory, it now has 256Mb.  Xubuntu installed easily, and I'm actually writing this post from the laptop.  It just needs a new battery!  Thanks for everyone's input!

---

### Post by azk on 2007-03-29
Hi.
I just revived my 5300 yesterday after I got 2x 256 sdram chips, runs hell of a lot better than the old 128 mb. After having sat through 250 updates I began searching for gpu drivers, I thought you would like to have those if you haven't already.
[http://www.s3graphics.com/en/resources/drivers/legacy/software_archive.jsp#id_290298drv](http://www.s3graphics.com/en/resources/drivers/legacy/software_archive.jsp#id_290298drv)

---

