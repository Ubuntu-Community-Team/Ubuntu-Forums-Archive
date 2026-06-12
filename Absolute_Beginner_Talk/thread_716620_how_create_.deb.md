---
title: "how create *.deb"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by etusha on 2008-03-06
hello all
im new in ubuntu and i like it 
and i like to help ubuntu user creating deb packet
i ask u experts if is any program that help me do that 
create deb from C++ and RPM 
and if i create deb where i have to upload it that user can access it

---

### Post by kpkeerthi on 2008-03-06
[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)
[http://ubuntuforums.org/showthread.php?t=2356](http://ubuntuforums.org/showthread.php?t=2356)

---

### Post by kpkeerthi on 2008-03-06
You can convert rpm to deb using **alien** (available in the repo)
See [http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/](http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/)

---

### Post by elvisd on 2008-03-06
Try deb creator to create deb files from scratch

[http://debcreator.cmsoft.net/]("http://debcreator.cmsoft.net/")

Hope this helps

---

### Post by PeterJS on 2008-03-06
The problem with checkinstall Debs is that you have to manually build the dependency tree for them. Which is a terrible pain to do. Distributing Debs, without proper dependencies is pretty much guaranteed to result in packages that fail to work. There's a proposal to create a spec to have check install handle the dependencies for you, but it's several versions out, if it ever gets implemented.

[http://brainstorm.ubuntu.com/idea/2445/](http://brainstorm.ubuntu.com/idea/2445/)

If you're planning on distributing the debs you'll want to use dh_make as mentioned in the above linked thread. Good luck, you're a braver man than I.

---

### Post by etusha on 2008-03-06
and any good way or program that help me find dependency

---

