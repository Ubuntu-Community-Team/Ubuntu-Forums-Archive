---
title: "How do you download a Tar.zg"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by -gabe-noob- on 2008-01-17
More spesificly for TestDisk, what do I press to install? :P I extracted it to my desktop but I'm lost from here .

---

### Post by forestpixie on 2008-01-17
[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

have a look here, make sure you have build essential installed first, and checkinstal can make it a bit easier later I think

```
sudo apt-get install build-essential checkinstall
```

---

### Post by hyper_ch on 2008-01-17
what do you want to install? Are you sure it's not in a repo or somewhere else available as .deb?

---

### Post by forestpixie on 2008-01-17
in fact it looks like testdisk is

```
sudo apt-get install testdisk
```

you can search using apt-get easily

```
sudo apt-cache search *packagename*
```

---

### Post by hyper_ch on 2008-01-17
for the search no sudo is needed

---

### Post by Omnios on 2008-01-17
Tarballls are fun tarballs are not that hard to install.

Try this link it may help a bit.

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

 Also deb packages are easier to maintain as if you add a repository for the deb it will upgrade it self when updates are available. 

 Also when using config and make you can use errors to see if you need any depends. Example error could not find ??? and look it up in snaptic.

---

### Post by -gabe-noob- on 2008-01-17
Thankyou all!

---

### Post by -gabe-noob- on 2008-01-17
after I use the apt-get install how can I get into testdisk?

---

### Post by oldos2er on 2008-01-17
Type "testdisk" in a terminal.

---

### Post by -gabe-noob- on 2008-01-17
I did that, geuss I should read the how-to on how to use it cause when I did that I had NO idea what to do

---

### Post by hyper_ch on 2008-01-18
if it's a command line program, you can access the manual pages:

```

man testdisk

```

---

