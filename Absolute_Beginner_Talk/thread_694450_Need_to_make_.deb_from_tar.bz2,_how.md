---
title: "Need to make .deb from tar.bz2, how?"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by webbie180 on 2008-02-12
[http://gmlive.googlecode.com/files/gmlive-0.20.tar.bz2]("http://gmlive.googlecode.com/files/gmlive-0.20.tar.bz2")

Can anyone show me how to make the above into a deb file?  Thanks.

---

### Post by hyper_ch on 2008-02-12
[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

---

### Post by webbie180 on 2008-02-12
Thanks.
I got this error while doing ./configure,
No package 'gtkmm-2.4' found
No package 'libglademm-2.4' found
And I cant find the packages in synatic....help, thanks.

---

### Post by hyper_ch on 2008-02-12
well, you have to install those then (manually)

---

### Post by HereInOz on 2008-02-12
Search for them in the repositories using Synaptic.  I think they are both there in some form or another.

---

### Post by jan quark on 2008-02-12
i think you need the development file

libglademm-2.4-dev

---

### Post by webbie180 on 2008-02-12
Cant find them in synatic......tried apt-get install too...but failed.

---

### Post by rfurman24 on 2008-02-12
Both of them are in synaptic when I search. You will need the dev versions.

---

