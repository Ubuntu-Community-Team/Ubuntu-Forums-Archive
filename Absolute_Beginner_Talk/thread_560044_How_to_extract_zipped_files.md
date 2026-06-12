---
title: "How to extract zipped files?"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by T4K3Z0U on 2007-09-25
I've downloaded an important file but it seems to be  zipped and I can't unzip it.
When I try it says "archive type not supported"

The file type is .r00 with like 22 files altogether.

I tried to send it to my windows partition but it tells me I don't have permission to copy, but when I looked at the permission list it seems I do have permission. 


So confusing, please help me access/extract this file.

---

### Post by misfitpierce on 2007-09-25
You can enable more archive types through repo's and EasyUbuntu also does this for you in archives... Add's more zip support and rar and so on. Easyubuntu found in sig.

---

### Post by bodhi.zazen on 2007-09-25
[http://ubuntuforums.org/showthread.php?t=476048](http://ubuntuforums.org/showthread.php?t=476048)

---

### Post by jalanbuntu on 2007-09-25
You should install a correct compression tool. May be those are not a zip files.
I dont know exactly what is the compression type for that file regarding to the .r00 extension :D

---

### Post by T4K3Z0U on 2007-09-25
> **misfitpierce said:**
> You can enable more archive types through repo's and EasyUbuntu also does this for you in archives... Add's more zip support and rar and so on. Easyubuntu found in sig.

How do I do that?

> **bodhi.zazen said:**
> [http://ubuntuforums.org/showthread.php?t=476048](http://ubuntuforums.org/showthread.php?t=476048)

I looked at this link but I no idea what to do. I cut and pasted the code into terminal and it came back saying "no such file or directory" I know its something simple I haven't done, just don't know what that simple thing is.

---

### Post by qpieus on 2007-09-25
yeah, those are not zip files. they are rar files. To unpack, install unrar:

sudo apt-get install unrar

After installing you install it, you should be able to right click on the first file (it ends in ".rar") and see a selection for extract.

Note that some rar files made with a newer version of rar have a different filename pattern - they are filename.part01.rar, filename.part02.rar, etc. The files you have look to be the older filename pattern. The first file is filename.rar, the second part is filename.r00, the third is filename.r01, etc.

---

### Post by T4K3Z0U on 2007-09-25
> **qpieus said:**
> yeah, those are not zip files. they are rar files. To unpack, install unrar:

sudo apt-get install unrar

After installing you install it, you should be able to right click on the first file (it ends in ".rar") and see a selection for extract.

Note that some rar files made with a newer version of rar have a different filename pattern - they are filename.part01.rar, filename.part02.rar, etc. The files you have look to be the older filename pattern. The first file is filename.rar, the second part is filename.r00, the third is filename.r01, etc.

This worked Thank-you kindly.

---

### Post by nikoPSK on 2007-09-26
Aww. Someone beat me to it. But, yes unrar is a great tool:KS

---

### Post by jalanbuntu on 2007-09-26
Maybe you should also install other archiving tool like ace and 7zip.
I'm using automatix2 to install those applications.

---

### Post by nikoPSK on 2007-09-26
7-zip wasn't working for me...:confused:

---

