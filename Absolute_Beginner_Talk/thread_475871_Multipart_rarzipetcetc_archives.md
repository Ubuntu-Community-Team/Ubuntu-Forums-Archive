---
title: "Multipart rar/zip/etc/etc archives"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by futare on 2007-06-16
Hi Guys, hope someone knows how to solve this.... I have a file thats compressed and consists of a number of compressed files.  Ie: file1.001, file2.002 and so on and do on... The only problem is that the archive manager is not able to extract and reconstruct it all into one file.

if it helps, the file is a avi file thats split into many parts... I think its rar archives although I would have thought that rar/unrar would then recognize them.

any help/ideas would be much appreciated. :) :D

---

### Post by Skrynesaver on 2007-06-16
Try the following in a terminal, 
```

for i in  $(ls file?.???);do
cat $i  >>file.rar
done

```This will concatonate all the files into one file which you can then point the archive manager at. 
NOTE: You will have to have the rar/unrar package installed

---

### Post by zvacet on 2007-06-16
```
sudo aptitude install p7zip p7zip-full rar unrar
```

Right click on package and select **unpack here**

---

