---
title: "tar.gz"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by squeezycheese on 2007-08-24
Hi,

A son of my mothers friend has just set ubuntu up for me, however i cannot remember how to un tar tar.gz files.

I know i use the command xvzf ndiswrapper.tar.gz

Do i just input this in the terminal or is there more that is needed to be done?

Many thanks

---

### Post by henriette_holm on 2007-08-24
Hi.
You do

tar -xzvf *.tar.gz

in a terminal as far as I remember.

---

### Post by squeezycheese on 2007-08-24
With * being the file name?

---

### Post by philinux on 2007-08-24
just double click on the file

---

### Post by squeezycheese on 2007-08-24
lol, oh so simple yet oh so effective :)

Thanks both of you

---

### Post by henriette_holm on 2007-08-24
yes, exactly. An example:

$ tar -xzvf ndiswrapper.tar.gz

should extract everything into a sub directory of the directory your in.

/Henriette

---

### Post by kerry_s on 2007-08-24
you need to also be in the same place as the *.tar.gz. use " ls " in the terminal to see whats there. cd is to change directorys(ex: cd Desktop)

---

### Post by squeezycheese on 2007-08-24
Okey, I tried those command lines and they didnt work.

Could someone write me a step by step fool proof guide to installing ndiswrapper for dummies please?

---

### Post by henriette_holm on 2007-08-24
Where you not able to extract the files? In plain english - do you have a new library containing the ndiswrapper installation files?

Anyway, maybe you should try to have a look at the beginning of this howto:

[http://ubuntuforums.org/showthread.php?t=297092&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=297092&highlight=ndiswrapper)

I must say that I have no experience using ndiswrapper myself.

/Henriette

---

### Post by philinux on 2007-08-24
Isn't ndiswrapper in synaptic package manger?

---

### Post by squeezycheese on 2007-08-24
Yes, it is, but i tried installing from the package manager but it came up with an error. and a long list of web urls. 

If needs be i can go back try again and c+p the errors

---

### Post by henriette_holm on 2007-08-24
It might be a good idea to post the errors.

---

### Post by squeezycheese on 2007-08-24
I am now trying the instructions in that link you posted. If these do not work then i will get the errors.

---

