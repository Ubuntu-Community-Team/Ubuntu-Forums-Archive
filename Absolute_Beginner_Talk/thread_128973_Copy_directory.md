---
title: "Copy directory"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by CookieOrc on 2006-02-12
Hey I am using wine to play a game called Gunz. The program is not letting me do the automatic update so I am manually replacing the files. Which are on 
/media/sdc1/Program\ Files/MAIET 

and i want to move them to
/home/cookieorc/.wine/drive_c/Program\ Files

but when ever i type the command
cookieorc@LinuxBox:/$ ```
sudo cp /media/sdc1/Program\ Files/MAIET /home/cookieorc/.wine/drive_c/Program\ Files
```
I get this error 
> cp: omitting directory `/media/sdc1/Program Files/MAIET'
It is not really an error but it appears not to be copying the directory. I have already tried to use the GUI with no success and this will show how bad i am with the command line

---

### Post by kaamos on 2006-02-12
```
sudo cp -a /media/sdc1/Program\ Files/MAIET /home/cookieorc/.wine/drive_c/Program\ Files
```
checking "man *command*" is often useful with stuff like this. :)

---

### Post by CookieOrc on 2006-02-12
lol yea... I knew the answer was goin to be somthing stupid and simple like my last post thats why I posted it here lol :twisted:

---

### Post by photismos on 2008-02-24
:-s artificial intelligence is no match for natural stupidity...wherever you may post apparently

---

