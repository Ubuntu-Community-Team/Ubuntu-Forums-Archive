---
title: "Opening a directory"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by 3rr0r on 2006-09-04
I copied one of my cd's to my hard drive, and I can see it there graphically, but I am trying to open it through terminal but I can't seem to do it.  I think it is because the folder name is 2 words.  How would I go about opening it?  I have pasted what was on my terminal below:

err0r@3rr0r:~$ ls
Circa Survive  Desktop  Docs  Examples  Firefox_wallpaper.png  Themes
err0r@3rr0r:~$ cd Circa Survive
bash: cd: Circa: No such file or directory
err0r@3rr0r:~$ cd Circa_Survive
bash: cd: Circa_Survive: No such file or directory
err0r@3rr0r:~$ cd Circa
bash: cd: Circa: No such file or directory
err0r@3rr0r:~$


(the CD Artist is "Circa Survive")  

Thanks !

---

### Post by annda on 2006-09-04
you need to "escape" spaces in terminal by \

in short:
```
cd Circa\ Survive
```

---

### Post by annda on 2006-09-04
it's also a good idea to use tab completion: type the first letter(s) and press TAB - the name will be completed for you.

if not, that means that there is more than one choice - press TAB again to list them, or type another letter and TAB again

---

### Post by 3rr0r on 2006-09-04
awesome, thanks!

---

### Post by 3rr0r on 2006-09-04
How would I go about moving a directory from my main hdd (sda3) to a fat32 share (sda4)? I don't know how to move directories inbetween hdd's.

---

### Post by annda on 2006-09-04
all your drives are mounted and listed in /media

just cd there, ls them all and use full path in you commands, e.g.

```
cp /media/sda3/temp/tmp.tmp /media/sda4/backup/
```

---

