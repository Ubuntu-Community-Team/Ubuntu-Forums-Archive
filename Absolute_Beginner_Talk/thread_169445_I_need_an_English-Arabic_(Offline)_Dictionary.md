---
title: "I need an English-Arabic (Offline) Dictionary"
date: 2006-05-02
forum: Absolute Beginner Talk
---

### Post by Isoss on 2006-05-02
I've got an online Dictionary .. but I need something that works offline.
I need it both Arabic-English and English-Arabic ... does anybody have a suggestion?

Thanks

---

### Post by cgjones on 2006-05-02
Try doing a search of the forums. This was the subject of a post a week or two ago.

---

### Post by matthew on 2006-05-02
I have not tried this, but I found it in a search on your behalf and it looks interesting. I have no idea how to use it or anything about it, but this might help you refine your search a bit.

[http://en.wikipedia.org/wiki/Freedict]("http://en.wikipedia.org/wiki/Freedict")
[http://packages.ubuntu.com/dapper/source/freedict]("http://packages.ubuntu.com/dapper/source/freedict")
[http://packages.ubuntu.com/dapper/text/dict-freedict-eng-ara]("http://packages.ubuntu.com/dapper/text/dict-freedict-eng-ara")

if you try it out and get it working, please post a follow-up as I and perhaps others would be interested

---

### Post by Isoss on 2006-05-02
I found an arabic-english dictionary in one of the links.  I downloaded the .deb file and tried to intall it with terminal and that's what it gave me:
```
isos@localhost:~$ sudo dpkg -i /home/isos/Desktop/dict-freedict-eng-ara_1.3-1_all.deb
(Reading database ... 90626 files and directories currently installed.)
Preparing to replace dict-freedict-eng-ara 1.3-1 (using .../dict-freedict-eng-ara_1.3-1_all.deb) ...
Unpacking replacement dict-freedict-eng-ara ...
Setting up dict-freedict-eng-ara (1.3-1) ...
   The parameter --locale=xx_YY.utf-8 was not set in your /etc/default/dictd,
   so after installing this package dictd may stop working.

```
What does that mean? and how can I solve this?

---

### Post by nanotube on 2006-05-02
well, it said "may" stop working. did you try it and see if it works? :)

---

### Post by Isoss on 2006-05-04
I can't find it ... and why wasn't it set in  /etc/default/dictd ???

---

### Post by Isoss on 2006-05-12
How can I run dictd? I can't find it's app icon, nor can I start it using terminal. dictd is listed among the packages list which I can get pressing <TAB> twice in terminal and it's there but can't get it to start!

I dunno whus wrong with this, but I am still open for more suggestions and recommendations.

---

### Post by majikins on 2008-03-18
Had same problem 
"The parameter --locale=xx_YY.utf-8 was not set in your /etc/default/dictd"
when I downloaded and installed dict-freedict-eng-swa

Just sudo vim /etc/default/dictd and uncommented 
DICTD_ARGS="$DICTD_ARGS --locale=en_US.utf-8"
ie took out the # that was in front of the line, saved and resinstalled dict-freedict-eng-swa .

Started gome-dictionary(working in offline mode) and the dictonary appeared.

:guitar:

---

