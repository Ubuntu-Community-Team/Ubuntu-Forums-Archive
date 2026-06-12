---
title: "how do I convert pictures to different format?"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by jw1405 on 2007-11-09
Using Ubuntu 7.10 Ce. I'm new to linux, and am having photo problems. I have pictures that I scanned with Xsane image scanner, and they came out as .pnm files. I need to convert them to .jpeg. how do I do this? Any help would be appreciated.

---

### Post by Maestro23 on 2007-11-09
> **jw1405 said:**
> Using Ubuntu 7.10 Ce. I'm new to linux, and am having photo problems. I have pictures that I scanned with Xsane image scanner, and they came out as .pnm files. I need to convert them to .jpeg. how do I do this? Any help would be appreciated.

If you have** gThumb** installed just goto: Tools>>Convert Format

---

### Post by carlosjuero on 2007-11-09
the easiest thing with XSane is to have the items scan into JPEG/TIFF format right from the get go (if you are doing a multi page project it is a different story).

But yeah, like Maestro said - you can use gThumb; GIMP might be able to help as well

---

### Post by jw1405 on 2007-11-09
Tanks to both of you. that worked like a charm.

---

### Post by Maestro23 on 2007-11-09
> **jw1405 said:**
> Tanks to both of you. that worked like a charm.

No prob man.  Please mark this SOLVED using the Thread Tools.

Thanks.:)

---

### Post by disturbedite on 2007-11-09
in kde/kubuntu you can just right click on images and go to Actions --> Convert image to PNG, JPEG, etc....

---

### Post by cherry316316 on 2007-11-11
> **disturbedite said:**
> in kde/kubuntu you can just right click on images and go to Actions --> Convert image to PNG, JPEG, etc....

how do you convert a large amount of files 
for example  i need

convert "filename".bmp to "filename".eps

so basically i dont want to change the file name and i have too many files 
so i want to write a for loop in command prompt.

thanks

---

### Post by cherry316316 on 2007-11-11
> **cherry316316 said:**
> how do you convert a large amount of files 
for example  i need

convert "filename".bmp to "filename".eps

so basically i dont want to change the file name and i have too many files 
so i want to write a for loop in command prompt.

thanks

heya , i found the solution while playing and googling :)

for img in all00*/*.bmp; do mogrify -format eps all00*/*.bmp; done

where my all bmp files are in all00* folders :)
that was quick and easy :)

---

