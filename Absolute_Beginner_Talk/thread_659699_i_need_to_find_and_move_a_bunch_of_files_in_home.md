---
title: "i need to find and move a bunch of files in /home"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by xuhhx on 2008-01-06
Ok, i have a folder in my /home which contains a bunch of other folders, and each of those folders contains a bunch of files. what i would like to do is to take all of the .jpg files form all of folders and move them to another folder. is there a command that would be able to do this? 

So, simply i would like to move all the .jpg's from '/home/graham/aaaaaa' to '/home/graham/Desktop/files'   


thx,
xuhhx

( if it helps here is a more visual layout of were i need to get the .jpg's from )
```
  /home/graham+
              |_aaaaaa*+
                       |_folder 1 *-contains .jpg's*
                       |_folder 2 *-contains .jpg's* 
                       |_folder 3 *-contains .jpg's* 
                       |_etc...
```
*aaaaaa is the actual folder name

---

### Post by mouseboyx on 2008-01-06
mv /home/graham/aaaaaa/(foldername)/*.jpg /home/graham/Desktop/files

---

### Post by xuhhx on 2008-01-06
bump**

and also I forgot to mention, but the files have to be renamed aswell so that they do not overlap

---

### Post by xuhhx on 2008-01-06
> **mouseboyx said:**
> mv /home/graham/aaaaaa/(foldername)/*.jpg /home/graham/Desktop/files
dident work

---

### Post by saj0577 on 2008-01-06
It is possible to do it but to do it so all the files are renamed as well that adds complications. I will try and come up with something for you though.

Saj

---

### Post by saj0577 on 2008-01-06
WIll their be many files with the samename or will their just be a few? I.e have you taken them all with the same camera so you have 50 folders of cannon01.jpg, cannon02.jpg. for example? Or do you just want to make sure you do not lose any pictures with the possibility of a few having the same names.

Saj

---

### Post by xuhhx on 2008-01-06
> **saj0577 said:**
> WIll their be many files with the samename or will their just be a few? I.e have you taken them all with the same camera so you have 50 folders of cannon01.jpg, cannon02.jpg. for example? Or do you just want to make sure you do not lose any pictures with the possibility of a few having the same names.

Saj

there is a lot. in each folder each .jpg is named *1.jpg, 2.jpg, 3.jpg, etc..*

---

### Post by erfahren on 2008-01-06
probably be better and easier to rename them before moving them (in two seperate steps)

---

### Post by xuhhx on 2008-01-06
> **erfahren said:**
> probably be better and easier to rename them before moving them (in two seperate steps)

good point

---

### Post by erfahren on 2008-01-06
check this out (in Synaptic)
> 
Complete batch renamer for Linux
GPRename is a complete batch renamer for files and directorys.
GPRename easily can replace, remove, insert, delete and number
consecutively files and directorys.

 Homepage: <http://gprename.sourceforge.net/>


---

### Post by erfahren on 2008-01-06
Mass Rename (mrename)

---

### Post by xuhhx on 2008-01-06
> **erfahren said:**
> check this out (in Synaptic)

ya, it works for renaming said files, but i still haft to go through and find all of the files that i dont want to be changed

---

### Post by xuhhx on 2008-01-06
this whole thing seems like it would be easier to just do it manually than to find a way to do it easier, :-k

---

