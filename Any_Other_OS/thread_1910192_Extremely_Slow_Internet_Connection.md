---
title: "Extremely Slow Internet Connection"
date: 2012-01-16
forum: Any Other OS
---

### Post by SoulMazer on 2012-01-16
Hello, I am a long time Linux user and I have recently run into an interesting problem. I just finished building my own computer yesterday and now have a Win7/Ubuntu 11.10 dual boot system running (as I did with my last computer). 

However, I seem to have one very big problem. In Ubuntu, my download speed on any site I visit is about 60 KB/s. On my old computer (both Linux and Windows) and on my new Windows installation, I get my expected 1.2 MB/s. I have tried both ethernet and two different wireless adapters to no avail. It took me 30 minutes this morning to download 15 megs of updates...completely unacceptable.

That being said, does anybody know what could be going on here? 

Thanks in advance.

(Note: I am actually running the latest Linux Mint, but seeing as it is very closely based on Ubuntu, I much prefer to ask on this forum.)

---

### Post by SoulMazer on 2012-01-16
Apparently this is a problem with my Z68 motherboard. Apparently the driver loaded by most Linux distros (Red Hat, Fedora, Ubuntu) is broken (R8169) and thus a working version should be used (R8168B).

See more here: [http://www.foxhop.net/realtek-dropping-packets-on-linux-ubuntu-and-fedora]("http://www.foxhop.net/realtek-dropping-packets-on-linux-ubuntu-and-fedora").

---

### Post by Silverflyer on 2012-01-16
I am glad I found this, I am about to build my own dual boot computer and was planning on using a Z68 motherboard as well.

---

