---
title: "partimage - 2 simple questions"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-07-31
i created a partition image, but in the path i saved it as backup7-31-06. i didn't put the .gz on the end. will that affect the restoring process? 

also, the partition was split into many images...say i burned them all to cd's, when i go to restore, how does that process take place? 


thank you for your patience!

---

### Post by jordilin on 2006-07-31
rename it, doing:
```
mv backup7-31-06 backup7-31-06.gz
```
Linux does not know about the extensions. If the file backup7-31-06 is really a compressed file, then doing:
```
file backup7-31-06
```
will tell you is a compressed file although it has no extension. The extensions are for you to remember that a file is really a txt or gz file.

---

### Post by shanepardue on 2006-07-31
awesome..thanks. so do you know the restore process? do i just restore each image and when i'm done, my partition is complete?

---

### Post by jordilin on 2006-07-31
> **shanepardue said:**
> awesome..thanks. so do you know the restore process? do i just restore each image and when i'm done, my partition is complete?
I don't know about the restoring process. I don't use Partimage to backup my data, but let's await if someone else has any idea on how to do it.:D

---

### Post by 1oki on 2006-07-31
> **shanepardue said:**
> awesome..thanks. so do you know the restore process? do i just restore each image and when i'm done, my partition is complete?

If this is a newly formated box, why dont you just play with it and figure it out... Wont have much to lose and you can than contribute it to the rest of us! :D 

-L

---

### Post by shanepardue on 2006-07-31
> **1oki said:**
> If this is a newly formated box, why dont you just play with it and figure it out... Wont have much to lose and you can than contribute it to the rest of us! :D 

-L

this isn't a newly formatted box in the least. it's customized to how i want it. if ever my machine gets hosed, i can fall back on a solid configuration.

has no one restored with partimage before?

---

### Post by 1oki on 2006-08-23
gottcha... never used partimage b4...

---

### Post by djsroknrol on 2006-08-23
Just mount the drives in the exact opposite of how you imaged the drive and your restore should go fine...the compressed (gz)image is more desirable as it naturally takes up less space...make sure that the partition is the exact same size to restore into...aysiu, another forum member, has an excellent link for info on how to use partimage...

---

### Post by shanepardue on 2006-08-23
awesome! everything worked fine awhile ago..i forgot to respond saying i got it working. thanks to all the responses!

---

