---
title: "Vim"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by flajus on 2006-11-05
hello can somebody help me i got a problem with "vim" . when i trying to write to he file (i'm using command :w!) and i get the following error:
"/usr/local/apache2/conf/httpd.conf"
"/usr/local/apache2/conf/httpd.conf" E212: Can't open file for writing

the first thing i thot that i need to become a root user BUT there comes another question how to become? i in terminal type "su" then i typed my "su" password and then I get the error: 
su
Password:
su: Authentication failure
Sorry.

I tried with "fakeroot" but fakeroot doesnt help. But heres the interesting thing when i type (for example) >> sudo dpkg -i ubuntuinstall.deb everything goes OK and then program will be succesfully installed. Sorry for my english but i think you understand what i want to ask:)

---

### Post by jordilin on 2006-11-05
you must do a sudo:
```
sudo vim nameoffile
```
and to write the file you must provide
```
ESC :w INTRO
```

---

### Post by thornomad on 2006-11-05
Are you opening a file on a local disk or opening a file over a network?

---

### Post by bsussman on 2006-11-05
You might want to search for the dozens (maybe 100s) of threads opened on this question.

The short answer is to use sudo.  The long answer is part of the socio-technical design of ubuntu, which installs without a root password set, to limit the poteitial damage that can be caused by use of the root account in most (inappropriate) situations, when temporary root privs, lasting for 1 command, will do.

BTW, you might want to try gvim - it is an interesting implementation of vim that mixes gui and traditional vi commandlineness.  Allows nice coloration, including background.  In this case, the command will be 'gksudo gvim <filename>' to acquire root privs.

Nautilus also has the ability to invoke editors 'as root'.

There are probably 16.354 more ways to accomplish your goal but I figure 3 should be enough for anybody.  :)

---

### Post by flajus on 2006-11-05
Thank You Bsussman:)!

---

