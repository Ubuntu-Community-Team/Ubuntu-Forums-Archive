---
title: "Linux Source Code??"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by Brahman on 2006-09-04
Is there any where (if this is even possible) where you can download the Linux source code not as an ISO file but a zip file and have the source code to mess with and somehow save or convert it to an ISO to make it bottable after modifying it?

---

### Post by Brahman on 2006-09-04
Does anyone know?

---

### Post by gary4gar on 2006-09-04
well why do u need source code??
users don't need it all! but developers use so if u are a developer u can join the ubuntu community
[http://www.ubuntu.com/developers](http://www.ubuntu.com/developers)

---

### Post by pufuwozu on 2006-09-04
I'm not sure that you'd be totally capable, but you should visit [http://kernel.org/]("http://kernel.org/") to download the Linux kernel source code.

---

### Post by bodhi.zazen on 2006-09-04
> **Brahman said:**
> Is there any where (if this is even possible) where you can download the Linux source code not as an ISO file but a zip file and have the source code to mess with and somehow save or convert it to an ISO to make it bottable after modifying it?

Yes it is possible.

[Linux from scratch](http://www.linuxfromscratch.org/)

---

### Post by Brahman on 2006-09-04
I just want the linux source code to look at and modify it just to see more about linux. 

Thanks for the link to Linux From Scratch.


So I can just download one of these and have the whole linux source code to mess with? [http://www.linuxfromscratch.org/lfs/downloads/stable/](http://www.linuxfromscratch.org/lfs/downloads/stable/)

---

### Post by kinematic on 2006-09-04
okey...now don't take this the wrong way but if you were a kernel hacker you wouldn't have to ask that question ;)

---

### Post by bodhi.zazen on 2006-09-04
> **Brahman said:**
> I just want the linux source code to look at and modify it just to see more about linux. 

Thanks for the link to Linux From Scratch.


So I can just download one of these and have the whole linux source code to mess with? [http://www.linuxfromscratch.org/lfs/downloads/stable/](http://www.linuxfromscratch.org/lfs/downloads/stable/)

Yes, and no. It depends on what you mean by "Linux" (this is hotly debated).
[Linux Name controversy](http://en.wikipedia.org/wiki/GNU/Linux_naming_controversy)

In a nutshell, "Linux" is a composite of a kernel + software + applications.

Kernel = Linux.
[kernel](http://kernel.org/)
Some people use "Linux" to refer only to the kernel.

Here "software" = GNU project + package management (.deb, RPM, pacman, emerge).
[GNU](http://www.gnu.org/)
Some people use "Linux" to refer to what should probably be called "GNU/Linux". I do this (ie when I say "Linux" I am referring to "Linux kernel + GNU" AKA GNU/Linux.

Kernel + GNU + package management (.deb vs RPM, etc) + appliations = Linux distribution (ie. Ubuntu, Red hat/Fedora, Arch, Gentoo).
I call this "Ubuntu" and not "Linux".
If this is what you want, see previous posts re: Ubuntu developers.

It will take some time to learn, obviously, but if you get through LFS you will have what you want.

---

### Post by Brahman on 2006-09-04
Thanks. 

 I'll go through the LFS. I want to use Linux, but I also want to see how it works to make a new distro like Ubuntu (someday lol). Thanks for the help and my apologies for so many questions so far.

---

### Post by Paul133 on 2006-09-04
Each distro then is just the GNU/Linux OS with certain apps (including package management apps, since there's no apt-get in Red Hat or non Debian-based distros), right?

---

### Post by bodhi.zazen on 2006-09-04
> **Paul133 said:**
> Each distro then is just the GNU/Linux OS with certain apps (including package management apps, since there's no apt-get in Red Hat or non Debian-based distros), right?

Yes, although there may be an exception out there (I am not aware of one, but I am no expert). See the "Linux Name controversy" link.

---

