---
title: "About apt-get."
date: 2005-08-28
forum: Absolute Beginner Talk
---

### Post by L.G. on 2005-08-28
Hi, all! I'm new user of Ubuntu and have a first questions about *apt-get.*
First, apt-get have *--download-only* option. How it work? I mean, this option allow to download package with dependencies or only package?
Second, were apt-get save downloaded packages?

TIA!


*P.S. Little description: I want to download some packages at work (were currently installed Ubuntu), write it on CD and then install on my home computer (were Ubuntu installed too).*

---

### Post by heimo on 2005-08-28
"Download only" option (for short flag -d) downloads also the dependencies. Packages are put to directory /var/cache/apt/archives/

More information on how to use apt-get:
[https://wiki.ubuntu.com/AptGetHowto]("https://wiki.ubuntu.com/AptGetHowto")

Local repository:
[http://www.ubuntuforums.org/showthread.php?t=42862](http://www.ubuntuforums.org/showthread.php?t=42862)

---

### Post by manicka on 2005-08-28
apt stores downloaded debs in

/var/cache/apt/archives

---

### Post by L.G. on 2005-08-28
**heimo, manicka** - thank you!

---

