---
title: "install font"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by heatrag on 2007-03-26
I have downloaded a .ttf font and wish to place it in the truetype folder, /usr/shared/fonts/truetype from memory I think. I don't have permission, can someone please tell me the method of install please?

---

### Post by psyberpnk on 2007-03-26
if you are moving files with the terminal use the sudo command prior to moving the files.  That should allow you to type in your root password.  

```
 sudo mv .....
```

---

### Post by angryfirelord on 2007-03-26
Search Synaptic because your font is probably located in a group of fonts in a package. That way you avoid the whole "moving it to the right location" issue.

---

### Post by heatrag on 2007-03-29
ok, to understand how to move files I created file 'a' on the Desktop and am attempting to move it into the fonts folder. Can anyone explain the following for me please:
dad@dad-desktop:~$ sudo mv a/ ~/usr/share/fonts
mv: cannot stat `a/': No such file or directory
dad@dad-desktop:~$ sudo mv /home/dad/Desktop/a/ ~/usr/share/fonts
mv: cannot move `/home/dad/Desktop/a/' to `/home/dad/usr/share/fonts': No such file or directory

---

### Post by heatrag on 2007-03-30
I'm not suprised I haven't got a reply, I'm so far from the mark on that command, it was unix I think. Worked it out myself in the end, best way I understand it now. Should be:

$ cd Desktop
$ sudo mv a /usr/share/fonts

mv can change file names as well.

$ mv a ab

The file 'a' is changed to 'ab'. One of my pleasures in life now 'mv'

---

