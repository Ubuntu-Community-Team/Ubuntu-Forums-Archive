---
title: "How to get rid of redundant sudo:s when using latex and make?"
date: 2005-08-01
forum: Absolute Beginner Talk
---

### Post by kalle314 on 2005-08-01
I must be doing something wrong, because I frequently has to type sudo to make changes in my own user directory.

Every time I use a program that writes to other files my command fails if I dont type sudo before it.

(For example the programs make (c++ code) or latex (tex files).)

[COLOR=SlateGray]
22:11:24 $  latex presentation.tex
This is e-TeX, Version 3.14159-2.1 (Web2C 7.4.5)
entering extended mode
! I can't write on file `presentation.log'.
Please type another transcript file name:
[/COLOR]

This can't be what it's supposed to be like, can it? 
(I can run the programs without problem if I run them from the root or if i type sudo before, but that is a bit inconvenient.)

---

### Post by poofyhairguy on 2005-08-01
[QUOTE=kalle314]I must be doing something wrong, because I frequently has to type sudo to make changes in my own user directory.

Every time I use a program that writes to other files my command fails if I dont type sudo before it.

(For example the programs make (c++ code) or latex (tex files).)

[COLOR=SlateGray]
22:11:24 $  latex presentation.tex
This is e-TeX, Version 3.14159-2.1 (Web2C 7.4.5)
entering extended mode
! I can't write on file `presentation.log'.
Please type another transcript file name:
[/COLOR]

This can't be what it's supposed to be like, can it? 
(I can run the programs without problem if I run them from the root or if i type sudo before, but that is a bit inconvenient.)[/QUOTE]

use the root terminal?

---

### Post by kalle314 on 2005-08-01
[QUOTE=poofyhairguy]use the root terminal?[/QUOTE]

Yes, that works of course, but I thought there had to be another more convenient and elegant solution.    :confused:

---

### Post by GilGalad on 2005-08-01
[QUOTE=kalle314]Yes, that works of course, but I thought there had to be another more convenient and elegant solution.    :confused:[/QUOTE]
 First make sure that you are in your home directory (i.e. $HOME/username). Then type

sudo chown -R username:usergroup *
sudo chown username:usergroup ./

where username is your username and usergroup is your group (probably the same as your username). This makes the directory and all the files under it owned by you.

---

### Post by kalle314 on 2005-08-01
Thanks!  :) 

However, there is still a problem - that gives me rights to all **existent** files in my own home directory - but not to files I'm going to create later - so I will have to use that command every day just to avoid writing sudo so often.   :-?

---

### Post by kalle314 on 2005-08-02
I found the reason for the problem:

I was in a directory which I had copied from the windows partition, so the rights was automatically set to something different than usual, (-r-xr-xr-x).

---

