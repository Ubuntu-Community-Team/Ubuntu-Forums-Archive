---
title: "install shake 4.1 on ubuntu 9.04"
date: 2009-06-15
forum: Apple Hardware Users
---

### Post by 360degrees on 2009-06-15
Hi!
I know this thread seems to run endlessly across the internet. But none have provided a solution that works.

Can anyone help me install Shake 4.1 on Ubuntu 9.04 in a easy step by step way?

Just so that I don't make a mistake in the install.

Thanks

---

### Post by cyberdork33 on 2009-06-16
> **360degrees said:**
> Hi!
I know this thread seems to run endlessly across the internet. But none have provided a solution that works.

Can anyone help me install Shake 4.1 on Ubuntu 9.04 in a easy step by step way?

Just so that I don't make a mistake in the install.

Thanks
Isn't Shake an extension for Final Cut? I don't think that it (or Final Cut) will run in Ubuntu.

---

### Post by 360degrees on 2009-06-16
No shake is a standalone application. Last build 4.1 was for OSX and linux, fedora core.
But Ive seen it work on ubuntu 7.1 and above.

And I wouldn't want to invest in a Mac just for this one app.

---

### Post by drws on 2009-07-27
To get Shake (version 4.10.0606) running in Jaunty I did this...
(As root)
[FONT="Courier New"]apt-get install libx11-6
cd /usr/lib
ln -s libxcb.so libxcb-xlib.so[/FONT]

The new libxcb seems to provide the libxcb-xlib requirement now.
The libx11-6 is also a requirement for running shake (provides /usr/lib/libX11.so.6.2.0)
:D

---

### Post by decoherence on 2009-07-27
Hi.

I am jealous of you both.

That is all ;)

---

### Post by tripundra on 2009-07-27
Uau... $4000 for a software is a lot...
I'm jealous-... I can't afford the $5000 for CADWork (timber-frame)!

;)

---

