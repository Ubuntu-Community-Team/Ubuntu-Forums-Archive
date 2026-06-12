---
title: "stepmania compile"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by Takuhari on 2007-12-27
I was wondering how can i compile stepmania...

i tried make
but there is no make file

and i tried automake --add-missing and automake
i believe --add-missing is suppose to make the makefile...

im still new at this... can anyone help?

---

### Post by SOULRiDER on 2007-12-27
Head to [www.getdeb.net](www.getdeb.net) im sure i've seen some DEB files for stepmania there so you won't have to compile it, just download and install.

---

### Post by Takuhari on 2007-12-28
I have a copy that is compiled and works properly...

I want to be able to compile this game on my own:popcorn:

---

### Post by jken146 on 2007-12-28
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)  has a section explaining how to do this.

---

### Post by Perfect Storm on 2007-12-28
> **Takuhari said:**
> I was wondering how can i compile stepmania...

i tried make
but there is no make file

and i tried automake --add-missing and automake
i believe --add-missing is suppose to make the makefile...

im still new at this... can anyone help?

What file does it contains?
```
 cd <into the folder>
ls -a
```

---

### Post by Takuhari on 2008-01-02
I was working with it and doing some research...
I almost got it to compile... after modding the genorated code...
i have a feeling that i am typing the incorrect commands to genorate codes properly...

can anyone tell me the proper commands to compile this game?

---

### Post by Takuhari on 2008-01-07
I figured out that all of the undefined refrence to... where all defined in the .m4 files in stepmania/autoconfig/m4/ 
hmmm... does anyone know how to use these?..

---

