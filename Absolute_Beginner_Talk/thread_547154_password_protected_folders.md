---
title: "password protected folders?"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by moose4204l on 2007-09-09
I know this question has been asked and I know what people typically say, but I have not read a satisfiable answer yet.

Basically, I want to know if there is a way to put a password on a particular folder so no one can open it. 

I have one account and I am at college. I have a folder that contains personal files that I dont want anyone to see, especially my girlfriend, Adult oriented. They dont know about running a live cd nor would they go to that extreme. But my girlfriend frequently uses my laptop but I dont want her accidentally running into the folder&#347; contents. 

So is there anyway to just put a basic password protection on a folder?

:guitar: rock on!

---

### Post by rfruth on 2007-09-09
Right click on the folder then properties & change permissions (or chmod using CLI) :)

---

### Post by SOULRiDER on 2007-09-09
You could always create a new user and store the files in a hidden folder in that user's home directory which is protected from other uses ALTHOUGH if you sudo you can see everything...

---

### Post by matthew.lns1 on 2007-09-09
You could make a guest account and have everyone else login on that or you could change the ownership of the file using "sudo chown root filename"  and then "sudo chmod g-r filename" . That way, only if you are root can you access the files. BTW, you have to open a terminal to run all those commands.

---

