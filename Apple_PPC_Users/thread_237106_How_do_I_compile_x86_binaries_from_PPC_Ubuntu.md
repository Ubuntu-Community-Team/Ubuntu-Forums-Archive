---
title: "How do I compile x86 binaries from PPC Ubuntu?"
date: 2006-08-15
forum: Apple PPC Users
---

### Post by rattboi on 2006-08-15
Hi,

I'm not a new Ubuntu user, but I've run into something I haven't found an answer to yet. I do some stuff with Xbox Linux, and I was able to compile in the past using my roommmate's computer w/ x86 Ubuntu. Now, he moved out, and I only have my mac mini now. If anyone could point me to a guide about setting up a cross-compiler, I'm pretty sure I could follow it.

Thanks for the help

---

### Post by avtolle on 2006-08-15
I would suggest posting in the Programming Talk subforum for assistance. Good luck.

---

### Post by mlind on 2006-08-15
You'll have to build toolchain for the target architechture. I think Scratchbox project is the easiest way.
I would probably create a chroot sandbox and use [http://www.mobilab.unina.it/Resources/crosscompilerHOWTO.html](http://www.mobilab.unina.it/Resources/crosscompilerHOWTO.html) as reference to build the necessary packages.

---

### Post by rattboi on 2006-08-15
mlind, thanks for that link. I actually found it before reading your post, and I'm on the step for building binutils.

As for what you said about the Scratchbox project and creating a chroot sandbox, I don't really follow. Could you explain?

---

### Post by rasec on 2006-08-15
You'll want to make sure that you're using the same version of gcc that you xbox uses (or at least the version of gcc the distro used), especially for c++ programs, because the ABI has been known to change from one revision to another. 

mlind, while we're on the topic of cross-compiling, do you know if you can cross-build deb packages? My powerbook takes forever to compile any moderate size packages, and the kernel easily takes over 20 minutes with the default config. I have dual core Athlon X2 that should considerably reduce the compile time if I could use it. Also, do you know if pbulder takes advantage of distcc? If it does, I should be able to set up a cross-compiler that way.

---

### Post by rasec on 2006-08-15
rattboi, if Scratchbox doesn't work out for you, you might want to give crosstool a try. I tried it once with moderate success a while back ago. It won't build debs though. Its just a script to build a compiler toolchain.

[http://kegel.com/crosstool/](http://kegel.com/crosstool/)

---

### Post by rattboi on 2006-08-15
Ok, I'm trying crosstool, because I'm not so sure about scratchbox, and the instructions say the host is supposed to be x86. Crosstool doesn't care, according to the instructions, so I'll try that.

---

### Post by rattboi on 2006-08-15
rasec, what you said about using the same version of gcc, is that because of how it links to the libraries? I assumed if I static-linked, I would be safe. Also, I'm just using C, so I think I should be safe. I think xbox is using gcc 3.3 or 3.4, and the cross compiler is set up for gcc 3.4.3. Well, I guess all I can do is see if it works

---

### Post by rasec on 2006-08-15
Yeah, its a library issue. Those gcc versions should be compatible. Let me know how it works out for you.

---

### Post by mlind on 2006-08-16
> **rasec said:**
> 
mlind, while we're on the topic of cross-compiling, do you know if you can cross-build deb packages? My powerbook takes forever to compile any moderate size packages, and the kernel easily takes over 20 minutes with the default config. I have dual core Athlon X2 that should considerably reduce the compile time if I could use it. Also, do you know if pbulder takes advantage of distcc? If it does, I should be able to set up a cross-compiler that way.


I bet it's possible. You can pass options to dpkg-buildpackage via pbuilder. I was just reading [http://www.emdebian.org/tools/crosstools.html](http://www.emdebian.org/tools/crosstools.html).
Looks kinda complex, but interesting.

---

### Post by rattboi on 2006-08-17
crosstool built properly, but I haven't yet tried compiling for the xbox yet. At least it built though.

---

