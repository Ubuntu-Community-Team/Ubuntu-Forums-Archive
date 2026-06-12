---
title: "Help with ISO Problems"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by Dakota42784 on 2007-11-01
I have ISO Master Program Installed, but notice things I can't do in ISO Master that I could do in ULTRA ISO  in Windows SUCH AS:

After making your Image file in Ultra ISO,...........If you click on the Image file you can view all the files that are inside of the Image................such as setup, autorun,etc,etc & tell what is there.

I cannot see those files in ISO Master??????         I have to go back to windows & open up Ultra ISO to view files & want to stay in Linux & do it all here.

Please help. 

---

### Post by taurus on 2007-11-01
If you want to look at your **filename.iso**, just mount it and then you can access it.

Applications -> Accessories -> Terminal
```
sudo mkdir /media/iso
sudo mount -t iso9660 **filename.iso** /media/iso -o loop
```
Now, you can browse over to /media/iso with nautilus and see everything in there.

---

### Post by Pumalite on 2007-11-01
[http://ubuntuforums.org/archive/index.php/t-212605.html](http://ubuntuforums.org/archive/index.php/t-212605.html)

---

