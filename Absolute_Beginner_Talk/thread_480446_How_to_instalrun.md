---
title: "How to instal/run"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by GoranI on 2007-06-21
I am new in linux world. I downloaded program "Nvu"- WYSIWYG editor. It comes in tar.bz2 format. I unpacked it, an on desktop I have folder with many executables, shell scripts, libraries and program folders. I don`t know how to install it or run it, as I told I work on Ubuntu second day.

If anybody can help - thanks !

---

### Post by swoll1980 on 2007-06-21
yor best bet is to see if sypatics pakage manager offers it . if it does not make a request, because some times what you see isn't always what you get.

---

### Post by swoll1980 on 2007-06-21
try this command in a terminal     

sudo aptitude install nvu
 
see if that works it will ask you for a pswrd you wont see it while your typing it but it's there
if you don't know how to open a terminal it's in your menu under applications>accesseries

---

### Post by Tyke91 on 2007-06-21
first you should probably type 

```
sudo aptitude update
```

to make sure everything is good to go, then 

yea, sudo aptitude install nvu would probably be best


EDIT: nvu is not available from the repos, doing the above wont work :(

you'll have to install manually

---

### Post by Tyke91 on 2007-06-21
have you tried Amaya 9.53?

it's available in the add/remove programs list and it looks similar to nvu

---

### Post by GoranI on 2007-06-21
I will try this program, byt anyway, I would like to know how to install manually, ;)

---

### Post by GoranI on 2007-06-21
> **GoranI said:**
> I will try this program, byt anyway, I would like to know how to install manually, ;)

Also I would like to know how to run it...

---

### Post by swoll1980 on 2007-06-21
to run it you would hit alt f2 and type the name of the ap in the run command
as far as installing it that depends on a lot of things are there install instructions on the site that you downloaded it from?

---

### Post by GoranI on 2007-06-21
> **swoll1980 said:**
> to run it you would hit alt f2 and type the name of the ap in the run command
as far as installing it that depends on a lot of things are there install instructions on the site that you downloaded it from?

There is no install instruction, also in the prog folder I did not found any instruction.

---

### Post by Tyke91 on 2007-06-21
which version did you download?

you want one thats preferably customized for ubuntu, or at least debian. getting a .deb file would be amazing since those auto install/run if you double click them

---

### Post by Tyke91 on 2007-06-21
another problem might just be the website... i can't even download most of these links, they just keep freezing or in the case of the .deb package, they delete themselves. are you sure you have an uncorrupted copy of this file to begin with?

---

### Post by Tyke91 on 2007-06-21
alright, i can tell you that downloading the .deb package from this link should work

[http://www.nvu.com/download/nvu-1.0.ubuntu.5.04.deb](http://www.nvu.com/download/nvu-1.0.ubuntu.5.04.deb)

---

### Post by Vencislago on 2007-06-27
Worked with me!
Thanks :popcorn:

---

