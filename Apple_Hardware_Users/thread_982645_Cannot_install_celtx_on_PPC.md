---
title: "Cannot install celtx on PPC"
date: 2008-11-14
forum: Apple Hardware Users
---

### Post by jorel314 on 2008-11-14
Hello,

I'm new to Linux and I've been trying to install celtx on my iBook G4 running Xubuntu 8.10.

I downloaded the Linux version of celtx here:
[http://celtx.com/download.html](http://celtx.com/download.html)

After extracting the file and navigating to the directory I ran this command:
./celtx

It gives me this error:
./celtx-bin: 1: Syntax error: "(" unexpected

I also tried downloading the source.

After extracting the file and navigating to the directory I ran this command:
./configure

It gives me this error:
configure: error: --enable-application=APP is required

Any help would be much appreciated.  Thanks!

---

### Post by stream303 on 2008-11-15
Are you sure they offer a PowerPC version which is what your ibook is? - I can't seem to find it on the download page.

---

### Post by jorel314 on 2008-11-15
I just downloaded the version that says Linux.

I was under the impression that since it uses XUL it would be able to run on any platform that Firefox can run on.  Kind of like how Java apps can run on any platform that has a JVM.

Please correct me if I am mistaken.  Thanks!

---

### Post by stream303 on 2008-11-15
Yep - In most cases, Linux is destined for Intel/AMD X86 / 64, and special compilation is needed for the PPC cpu platform.

That's one reason there aren't any vendor-native ppc apps for flash or other programs - ppc is a minority Linux port these days....

---

### Post by jorel314 on 2008-11-15
Darn.  

So how would one go about specificially compiling the source for PPC and creating a .deb?  If someone could point me in the right direction, I think it would be worthwhile for me to learn.

---

### Post by stream303 on 2008-11-15
Celtx looks to be a very specialist distribution, so perhaps your best bet might be to get in contact with the project leaders and see if they are interested in a ppc port of it.

It is much more involved than just recompiling a kernel for ppc.

I think they'd probably welcome a port, and maybe the best place to start would be to get in contact with our PPC-Forum users over at Gentoo, since the main attraction is compiling most everything to meet your needs.  From there, you might be able to assist the Celtx project with a port.

[http://www.gentoo.org/](http://www.gentoo.org/)

They have some very helpful and knowledgeable ppc users and team leaders.

---

### Post by jorel314 on 2008-11-19
Thanks for the options.

---

