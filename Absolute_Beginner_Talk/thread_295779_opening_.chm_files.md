---
title: "opening .chm files"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by cptjaben on 2006-11-08
I just recently got The official ubuntu book, I was expecting to see it as a .pdf, but instead it's a .chm. Does anyone know how to run .chm files in ubuntu?

---

### Post by Ecthelion on 2006-11-08
gnochm is the gnome chm reader...

You can find it in synaptic or [here]("http://gnochm.sourceforge.net/")

---

### Post by bodhi.zazen on 2006-11-08
Try xchm

---

### Post by cptjaben on 2006-11-08
Thanks for the advice

---

### Post by GStubbs43 on 2006-11-08
Isn't chm a Microsoft proprietary format? Where did you get the book as a chm? but yeah, I'd use gnochm if you're on gnome. :)

---

### Post by funrider on 2006-11-08
> **GStubbs43 said:**
> Isn't chm a Microsoft proprietary format? Where did you get the book as a chm? but yeah, I'd use gnochm if you're on gnome. :)

I would like to ask the same question. Is your "official book" really an official one?

I was trying to set up that xchm or other program and it was a pain. This required C++ complier or Perl or other program and I gave it up. Is there really any stable chm viewer out there?

---

### Post by GStubbs43 on 2006-11-08
> **funrider said:**
> 
I was trying to set up that xchm or other program and it was a pain. This required C++ complier or Perl or other program and I gave it up. Is there really any stable chm viewer out there?

Have you tried ```
sudo aptitude install gnochm
``` You don't need to compile anything. :)

---

### Post by Synikk on 2006-11-08
> **cptjaben said:**
> I just recently got The official ubuntu book, I was expecting to see it as a .pdf, but instead it's a .chm. Does anyone know how to run .chm files in ubuntu?

Arrr there matey ;) 

I've found that xCHM displays CHM files better than GnoCHM does, for some reason.

I hate CHM files...

---

### Post by bodhi.zazen on 2006-11-08
Likewise, I had problems with gnochm !

```
sudo aptitude install xchm
```

[how to install xchm](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Compiled_HTML_Help_.28CHM.29_Viewer_.28xCHM.29)

Try both !```
sudo aptitude install gnochm xchm
```

---

### Post by GStubbs43 on 2006-11-08
> **bodhi.zazen said:**
> Likewise, I had problems with gnochm !

```
sudo aptitude install xchm
```

[how to install xchm](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Compiled_HTML_Help_.28CHM.29_Viewer_.28xCHM.29)

Try both !```
sudo aptitude install gnochm xchm
```

aye. I didn't know xchm was in the repos.

---

### Post by mrli on 2006-11-15
Hi, I have a similiar problem with chm file. I have tried both

```
sudo aptitude install xchm
```

and

```
sudo aptitude install gnochm
```

but i get this message that says it cant find any package with name or description matched...

I enabled both multiverse and universe repositories.

Any help would be greatly apppreciated.

---

### Post by bodhi.zazen on 2006-11-15
Downlad the .deb from here: [xchm](http://packages.ubuntulinux.org/dapper/x11/xchm)

---

