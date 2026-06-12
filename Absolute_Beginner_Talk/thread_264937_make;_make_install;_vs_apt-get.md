---
title: "make; make install; vs apt-get"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by jmacdonagh on 2006-09-25
I'm just beginning working with Ubuntu although I have had previous experience with it. I'm wondering how well standard make files work with apt. Let me explain.

I want to start Mono development, and so the first thing I need to do is get the compiler and runtime on my system. Now, I have two routes. First, I can get the latest stable build installed on my system via apt. Alternatively, I can download the latest stable source and compile it myself (with a simple make and then make install). The question is, will "make install" update apt to let it know that mono is installed on my system? If I use apt to get a package that needs mono, I don't want apt to go ahead and download it again and possibly cause conflicts.

I would test this out on my own but I'm having trouble compiling mono, and I don't want to go through the entire process for nothing.

Thanks,
Johann

---

### Post by aysiu on 2006-09-25
I think you want *checkinstall*:
[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

---

### Post by lamego on 2006-09-25
> The question is, will "make install" update apt to let it know that mono is installed on my system? If I use apt to get a package that needs mono, I don't want apt to go ahead and download it again and possibly cause conflicts.
No, apt only knows about .deb based installations, also even if you use checkinstall to create a new deb package from source it may conflict if you install a mono based app which will rquire a mono package which may conflict with the one you have manually installed.
Since you have this question (not much experience) I do strongly advise you to keep with the apt version.

---

### Post by Railsbuntu on 2008-03-18
What's the point in using "checkinstall" when we have "apt-get source" available? Is the latter flawed? :confused:

---

