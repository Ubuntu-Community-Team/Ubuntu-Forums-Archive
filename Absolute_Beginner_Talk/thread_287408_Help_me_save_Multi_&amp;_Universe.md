---
title: "Help me save Multi &amp; Universe"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by sarum on 2006-10-28
Can somebody please help me out here. It says 'the following 4 lines'. I can see 3 boxes and five lines; I've just installed Dapper on a 2nd hand computer and would like try and get things right first time. Thanks to those who reply...........Sarum.[IMG]4 Lines.bmp[/IMG]



The image is copied from The Unofficial Ubuntu site, which I use a lot.

---

### Post by Anonii on 2006-10-28
> **sarum said:**
> Can somebody please help me out here. It says 'the following 4 lines'. I can see 3 boxes and five lines; I've just installed Dapper on a 2nd hand computer and would like try and get things right first time. Thanks to those who reply...........Sarum.[IMG]4 Lines.bmp[/IMG]



The image is copied from The Unofficial Ubuntu site, which I use a lot.
Try uploading your photo or attaching it in your post.

From what you can see, your screencap is not viewable.

Thanks :/

---

### Post by sarum on 2006-10-28
OOps, so sorry about that, not tried adding an image before. I've copied it on to a text ed: which is not as clear as the photo; but I hope you can understand the problem. Cheers Sarum.
Paste the following four lines into the box and click Add Repository, one line at a time: 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
To refresh the list of known packages (equivalent to apt-get update) 
Edit Menu -> Reload Package Information

---

### Post by Anonii on 2006-10-28
> **sarum said:**
> OOps, so sorry about that, not tried adding an image before. I've copied it on to a text ed: which is not as clear as the photo; but I hope you can understand the problem. Cheers Sarum.
Paste the following four lines into the box and click Add Repository, one line at a time: 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
To refresh the list of known packages (equivalent to apt-get update) 
Edit Menu -> Reload Package Information
Let me make it clearer via the command line. (I dont know how to use the GUI.) I'll tell you how to do the exact thing using the command line, you can continue using the GUI like before ,after that.

Open the command line, and execute:

```
sudo gedit /etc/apt/sources.list 
```

And then add this:

> 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main


In the end of the file. 

Save it. And the execute the command:

```
 sudo apt-get update 
```

---

