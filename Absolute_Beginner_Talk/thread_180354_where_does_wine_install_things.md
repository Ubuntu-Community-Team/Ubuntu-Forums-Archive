---
title: "where does wine install things?"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by shutupimpoor on 2006-05-22
it says its in C:/Program Files/ etc I am trying to install project 64. I can't find the files though. Where does wine install files? I have used search but nothing shows up

edit (SOLUTION):
[QUOTE=Stinger]
As mostwanted pointed out it's a hidden folder named ".wine" ( without the quotes), go to your home folder with nautilus and view &#8594; hidden files.
And the path to your programs is:
 ~/.wine/Program Files/
hope it helps :)[/QUOTE]

EDIT: New problem
has anybody gotten project 64 (nintendo 64 emulator) to run? I found the exe but nothing happens when i double click it and use wine emulator on it. For legalities: I only use games i own.

---

### Post by mostwanted on 2006-05-22
The wine c-drive can be found in ~/.c (a hidden folder, go to your home folder with nautilus and view &#8594; hidden files).

---

### Post by manicka on 2006-05-22
or it may be also be ~/.wine

---

### Post by Stinger on 2006-05-22
Almost right both of you ;) 

As mostwanted pointed out it's a hidden folder named ".wine" ( without the quotes), go to your home folder with nautilus and view &#8594; hidden files.

And the path to your programs is:

 ~/.wine/Program Files/

hope it helps :)

---

### Post by Koech on 2006-05-22
I think somewhere like /home/username/.wine/drive_c/Program Files/... or sth

---

### Post by Stinger on 2006-05-22
Well I couldn't get the path right myself , duh ! ](*,) 

Here is the right path:
 ~/.wine/drive_c/Program Files/

About your new problem.

> EDIT: New problem
has anybody gotten project 64 (nintendo 64 emulator) to run? I found the exe but nothing happens when i double click it and use wine emulator on it. 
I tried downloading [Project64]("http://www.pj64.net/main/") myself and here you can see what I got. 8)

---

