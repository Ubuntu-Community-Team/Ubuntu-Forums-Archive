---
title: "Macbook 4,1 resume from suspend problem in 9.10"
date: 2010-01-20
forum: Apple Hardware Users
---

### Post by vidmode on 2010-01-20
I've found that compiling the 2.6.32.4 kernel from source allows my macbook to come back from a suspend to ram, unlike the stock kernels that came with 9.10:
2.6.31-14-generic
2.6.31-15-generic
2.6.31-9-rt

I also tried these kernels from the Kernel PPA:
2.6.32-020632
2.6.33-999-generic

Kernel was built with the standard .config from 2.6.31-14-generic, with not much changed to update it to the new config answers. If anyone really wants, I can post it.

That said, I can't seem to find many people complaining that their macbook isn't resuming from suspend, so I may be alone in this issue.

---

### Post by linuxopjemac on 2010-01-21
can you post it as a .txt file as attachment ? I would like to post it on my website.

---

### Post by vidmode on 2010-01-24
Here's the .config file - but its for 2.6.32.4. According to the release notes for 2.6.32.5, you will want to build against that, as 

"All users of the 2.6.32 kernel series are very strongly encouraged to upgrade."
- [http://lwn.net/Articles/370818/](http://lwn.net/Articles/370818/)

I'll also stress that this is essentially a generic ubuntu build .config - it has many many modules selected that take a lot of time and space to build - doing a make clean in the kernel directory freed up 5gig of space. You'd be well advised to go through and remove modules that aren't required.

---

### Post by linuxopjemac on 2010-01-25
thank you very much, it found a new home on my site :)

---

### Post by vidmode on 2010-01-25
linuxopjemac: I don't mind my work being quoted/shared, but you really should give attribution on this page where you've copied what I've written, and written it up as being your own work:

[http://mac.linux.be/content/macbook-41-resume-suspend-kernel-config-2632](http://mac.linux.be/content/macbook-41-resume-suspend-kernel-config-2632)

---

### Post by linuxopjemac on 2010-01-25
That's done as of now.

---

