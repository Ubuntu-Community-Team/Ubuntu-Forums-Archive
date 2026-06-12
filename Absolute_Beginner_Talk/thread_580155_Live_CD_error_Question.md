---
title: "Live CD error Question"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by LinuxNewb092 on 2007-10-18
Hey guys, I have the Live Cd and I checked it for errors before I booted into it and it said there were none.  I then got to the desktop and it said, "error starting gnome settings manager", should I redownload it or is this a bug?

---

### Post by overdrank on 2007-10-18
> **LinuxNewb092 said:**
> Hey guys, I have the Live Cd and I checked it for errors before I booted into it and it said there were none.  I then got to the desktop and it said, "error starting gnome settings manager", should I redownload it or is this a bug?

Hi you can checksum the iso also
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
And these are the hashes 
ebf7ad055bc39634065daa10de980d7e *ubuntu-7.10-alternate-amd64.iso
9a4ae3cfd68911a861d094ec834c9b48 *ubuntu-7.10-alternate-i386.iso
61c87943a92bc7bf519da4e2555d6e86 *ubuntu-7.10-desktop-amd64.iso
d2334dbba7313e9abc8c7c072d2af09c *ubuntu-7.10-desktop-i386.iso
43ff753b260729b12c7d21d3a6db8c73 *ubuntu-7.10-server-amd64.iso
7d88cd87df509a740d9f47b9bbf1375e *ubuntu-7.10-server-i386.iso
5308a79f5e652edba5be84644ee14b09 *ubuntu-7.10-server-sparc.iso

:popcorn:

---

### Post by forestpixie on 2007-10-18
you could try burning it again as slow as you can first, and have you checked the md5sum - they're out there somewhere 

found these on a thread so you can check yours against it, courtesy of hackle577
> 
ebf7ad055bc39634065daa10de980d7e *ubuntu-7.10-alternate-amd64.iso
9a4ae3cfd68911a861d094ec834c9b48 *ubuntu-7.10-alternate-i386.iso
61c87943a92bc7bf519da4e2555d6e86 *ubuntu-7.10-desktop-amd64.iso
d2334dbba7313e9abc8c7c072d2af09c *ubuntu-7.10-desktop-i386.iso
43ff753b260729b12c7d21d3a6db8c73 *ubuntu-7.10-server-amd64.iso
7d88cd87df509a740d9f47b9bbf1375e *ubuntu-7.10-server-i386.iso
5308a79f5e652edba5be84644ee14b09 *ubuntu-7.10-server-sparc.iso

Edit - and while I was away searching someone snuck in with the same :)

---

### Post by LinuxNewb092 on 2007-10-18
thank you guys.  Could someone please tell me how to check them on linux, Im a newb and dont understand the way Ubuntu explains it.

---

### Post by overdrank on 2007-10-18
> **LinuxNewb092 said:**
> thank you guys.  Could someone please tell me how to check them on linux, Im a newb and dont understand the way Ubuntu explains it.

Hi I put the link in my post  ;)

---

### Post by LinuxNewb092 on 2007-10-18
Yes, I dont understand how to do the first step, could someone please specify what to do.  The files on my desktop.

EDIT: I went into K3B and it shows you the MD5 there.  Is 4X a slow enough speed?

---

### Post by maxxym on 2007-10-18
Burn it slow.. I had the same problem with my first copy..

I burned it at 10x. IT worked....

---

### Post by forestpixie on 2007-10-18
open a terminal 

```
cd Desktop
```

```
md5sum putthewholefilenamehere
```

and compare it to the list we've supplied

---

### Post by LinuxNewb092 on 2007-10-18
thanks for your reply.

---

### Post by forestpixie on 2007-10-18
problem not :)

---

### Post by LinuxNewb092 on 2007-10-18
Is 4X a slow enough burning speed?

---

### Post by overdrank on 2007-10-18
> **LinuxNewb092 said:**
> Is 4X a slow enough burning speed?

Hi and I would say if that is as low as you can go then yes. I just burned a gutsy cd at 4.7 and all is well. Good luck! :KS

---

### Post by LinuxNewb092 on 2007-10-18
Hi, Im actually having problems when I download the Gusty from Ubuntu, can you give me the link you downloaded it from please?

---

### Post by overdrank on 2007-10-18
> **LinuxNewb092 said:**
> Hi, Im actually having problems when I download the Gusty from Ubuntu, can you give me the link yo udownloaded it from please?

Sure why not lol
[http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu)
:lolflag:

---

### Post by JustinAlf on 2007-10-18
how do i earase this post>

---

### Post by overdrank on 2007-10-18
> **JustinAlf said:**
> how do i earase this post>

You can mark it solved by the link in my signature:KS.

---

