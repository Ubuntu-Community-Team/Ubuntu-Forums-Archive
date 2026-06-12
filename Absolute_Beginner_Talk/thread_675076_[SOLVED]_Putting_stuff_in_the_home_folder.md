---
title: "[SOLVED] Putting stuff in the home folder"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by Jeezus on 2008-01-22
...Is there some special reason I can't copy files and folders into my home folder?
I'm trying to set up the electricsheep screensaver, and when I try to copy the folder into my home directory, it tells me that I don't have permission...

...yes I'm very new to linux... =p

---

### Post by Tyke91 on 2008-01-22
are you trying to put things into ```
/home
``` or are you trying to put them into ```
/home/YOURUSERNAME
```
 
 
/home is the folder where all the different users' directories are held. /home/YOURUSERNAME is where you put your own files.
 
for instance, my username is mykola, so my home folder is /home/mykola.
 
 
you don't have access to the /home folder because it is owned by root. Most of your system is owned by root so that you don't give unwanted users acess to the rest of your system. you can get root privilages in a multitude of ways.

---

### Post by seventhc on 2008-01-22
How exactly are you trying to do it??
Are you sure it is your home directory that you're copying too?
You should be able to do whatever you want in your home directory.
Try saving to your desktop then under your home dir under places and see if you can just drag it in.

---

### Post by Jeezus on 2008-01-22
I understand now... I didn't before. "My" home folder is the folder with my username... 
got it!
Thanks!

---

### Post by mdpalow on 2008-01-22
> **Tyke91 said:**
> are you trying to put things into ```
/home
``` or are you trying to put them into ```
/home/YOURUSERNAME
```
 
 
/home is the folder where all the different users' directories are held. /home/YOURUSERNAME is where you put your own files.
 
for instance, my username is mykola, so my home folder is /home/mykola.
 
 
you don't have access to the /home folder because it is owned by root. Most of your system is owned by root so that you don't give unwanted users acess to the rest of your system. you can get root privilages in a multitude of ways.


Man! You helped '_Jeezus_' solve his problem! You are in... ;) [-o<

---

