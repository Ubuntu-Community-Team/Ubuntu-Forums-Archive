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

