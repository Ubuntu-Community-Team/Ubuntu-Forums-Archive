---
title: "rename multiples files by one name"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by edboq on 2006-11-15
Hi everyone

newbie with my new ubuntu, i was looking for a simple command which could make my work easier.

I've 900 album/cd/repertory of music in /home/edboq/music/
each album is in one repertory called for example : 

the cure - Starring at the sea 
u2 - war
pixies - doolittle

Note the names of my repertories (album) contain spaces.

In each repertory are located the songs (mp3) but also the cover of the album (which is one - ONLY ONE - picture whith an extension like be jpg JPG bmp... ) Note the name of this file contains also spaces.

My aim:

I would like to be able to rename all pictures named *.jpg *.bmp *.JPG with a name like picture.jpg so that each album has the same picture name

If i make in /home/edboq/music :

$ find . \( -name '*.jpg' -o -name '*.JPG' -o -name '*.bmp' \) -exec rename picture.jpg {} \;

it doesn't make the job

any comments will be highly appreciated :-D 

edboq

---

### Post by Naan Yaar on 2006-11-15
Try:

```

find . \( -name '*.jpg' -o -name '*.JPG' -o -name '*.bmp' \) -execdir mv {} picture.jpg \;
```

---

### Post by yurtfg89327tfg0o on 2006-11-15
First install mmv

sudo apt-get install mmv

Then

find <path> \( -name *.jpg -o -name *.JPG -o -name *.bmp \) -exec mmv -r {} picture.jpg \;

I hope that works

---

### Post by edboq on 2006-11-16
indeed i think , this is the right command
i try with different case and i'll keep you advised

thanks a lot

---

### Post by Arndt on 2006-11-16
> **Naan Yaar said:**
> Try:

```

find . \( -name '*.jpg' -o -name '*.JPG' -o -name '*.bmp' \) -execdir mv {} picture.jpg \;
```

I wonder if it's a good idea to rename a file something.bmp to something.jpg. Some utilities may look at the extension to decide what kind of image it is before looking into the file. But I don't know of any specific problems.

---

