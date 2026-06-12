---
title: "Download Critical Updates, burn to CD/DVD to install on offline systems"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by nvonkorff on 2007-03-26
Hi,

I have recently installed Ubuntu on my laptop and want to send a copy to my Dad, who lives on a farm, away from any kind of decent Internet connection.

I can give him the Installation CD, but I would like to download all the Critical Updates on my laptop first, burn those to DVD or CD and send that up to him, along with the installation CD.

Is there any simple way of doing this?

How would he then install all the updates if I can get them onto a CD? One by one, or would there be some way to make the CD/DVD act as a repository?

Cheers in advance.

Nick v K.

---

### Post by cowlip on 2007-03-26
Maybe [aptoncd ]("http://aptoncd.sourceforge.net/")could help?  It's in ubuntu's repos.  

He could install them by adding it as a repository, or doing

dpkg -i /media/dvd/*.deb

---

### Post by nvonkorff on 2007-03-26
Brilliant!

Thanks very much. I'll check it out.

Cheers,

Nick v K.

---

