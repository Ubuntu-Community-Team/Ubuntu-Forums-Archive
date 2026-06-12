---
title: "pSX deb?"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by chris062689 on 2008-02-07
I remember someone posting on this forum about having a psx .deb to download.
It included pSX and pSX-frontend.
It's not in the repos.  Does anyone know what I'm talking about?

---

### Post by talsemgeest on 2008-02-08
Is this what you want ```
wget -c http://mirrors.kernel.org/ubuntu/pool/universe/g/gtkglext/libgtkglext1_1.0.6-2.1ubuntu1_i386.deb
```

Hope this helps :)

---

### Post by chris062689 on 2008-02-12
No...
It was a deb (or two debs) that contained psx and psx-frontend.

---

### Post by Mud.Knee.Havoc on 2008-03-14
There was somebody hosting the pSX repo at [http://packages.dfreer.org](http://packages.dfreer.org), but I don't believe it's up anymore.  You can download pSX from its [official site]("http://psxemulator.gazaxian.com/"), though, and it doesn't take much to get it running.  Just remember to chmod +x the file pSX and run it by ./pSX

It might complain about not having libgtkglext-x11-1.0.so.0, you can install libgtkgltxt1-dev via synaptic or apt-get/aptitude.

---

### Post by chris062689 on 2008-03-27
Does anyone happen to have another respiratory I could download psx from?
I'd rather have it in a .deb format, that way I can easily uninstall it.

---

### Post by AnRa on 2008-03-27
You may have pSX contained in one single folder, it works flawlessly. :)

---

