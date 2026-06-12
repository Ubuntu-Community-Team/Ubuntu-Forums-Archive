---
title: "Convert PDF to JPG"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by agem on 2007-07-01
Does anyone know how I convert PDF files to a JPG format?

---

### Post by dpar on 2007-07-01
From what I read on Google, Imagemagick should do that.

---

### Post by agem on 2007-07-02
Thanks, Imagemagick does the trick.

It's as simple as 

```
 convert abc.pdf abc.jpg 
```

---

### Post by Rytron on 2008-03-13
> **agem said:**
> Thanks, Imagemagick does the trick.

It's as simple as 

```
 convert abc.pdf abc.jpg 
```

Hi,
Imagemagick is great.
Is there a terminal code to mass(batch) convert files?

---

### Post by Northsider on 2008-03-13
I'd also like to know.  I have a folder full of files I need converted...It'd be nice to do it all at once.

---

### Post by franket on 2008-03-18
> **Northsider said:**
> I'd also like to know.  I have a folder full of files I need converted...It'd be nice to do it all at once.

You can use command

convert *.pdf test.jpg

result test-0.jpg,test-1.jpg,... :)

---

### Post by PointyWombat on 2008-03-18
This will batch rename a bunch of pdf files to jpg files keeping their names and just change their extension.

```

for file in `ls *.pdf`
do
   convert $file `echo $file | sed 's/\.pdf$/\.jpg/'`
done

```


Note placement and types of quotes. Important.

---

