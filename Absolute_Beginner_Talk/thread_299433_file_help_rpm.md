---
title: "file help rpm"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by doh224 on 2006-11-14
hi all .. 

I don't think i'm abel to install rpm or deb files right.   
I sa convert rpm to deb. but wen install something, I only get a folder on my usr or home, I can't get the programs running.. 

:confused:        

-doh

---

### Post by LLRNR on 2006-11-14
In order to conver .rpm packages to .deb packages, you need a convertor utility called **alien**. Have you installed it already?
```
sudo aptitude update
sudo aptitude install alien
```
and then```
cd /path/to/file
sudo alien -i packagename.rpm
```

HTH,

LLRNR

---

### Post by dillbertdabomb on 2006-11-14
it's not exaxtly recomended, you should just lokk for the deb, what package anyway?

---

### Post by doh224 on 2006-11-14
pavcl_linux.rpm

the file is an antivirus.

and I am abel to convert. Thats not the problem. the problem is that when I've converted it to deb and installed it, there's only a folder? there's no program as there should be. 

or maybe it just me who can't get it started?

-mik

---

### Post by CatKiller on 2006-11-14
There are other anti-virus products in the repositories. And I seem to recall seeing instructions here somewhere for how to install Panda, but I could be mistaken.

How are you attempting to install your .deb? Also, as far as I know, installing from an aliened deb won't tell you about unmet dependencies.

---

### Post by doh224 on 2006-11-14
I just dobbel clik it. ?

---

### Post by CatKiller on 2006-11-14
> **doh224 said:**
> I just dobbel clik it. ?

You could try opening a Terminal window and typing the following commands:

```
cd /path/to/file/
sudo dpkg -i packagename.deb
```

You could still have dependency problems though.

You might also find it helpful to read [this page]("http://monkeyblog.org/ubuntu/installing/"), and [this page]("http://www.psychocats.net/ubuntu/security") for that matter.

---

### Post by ReaderRat on 2006-11-14
[**ClamAV AntiVirus For Ubuntu**](https://help.ubuntu.com/community/ClamAV)
[**Panda Antivirus for Linux**](http://www.pandasoftware.com/download/linux/linux.asp)

---

