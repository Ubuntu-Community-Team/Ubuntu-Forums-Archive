---
title: "Need program which tells me the file another program writes to"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by F0rdPr3f3ct on 2006-04-17
Hi,

I've the following problem. I'm developing a QT4 program. I managed to destroy my qt4 config by using the program "qtconfig" which is provided by the QT4 package. I need a program which tells me which files qtconfig writes to so I can restore my configuration.

tia, F0rd

---

### Post by nalmeth on 2006-04-17
I'm sorry I don't know how to help you, but this doesn't appear to be a *begginer *question. 
If you found the package's website, it might give you some details on how it behaves.
Perhaps it's in a hidden folder in your /home?
That's where a lot of your config files will be stored for various apps.
Assuming you are a beginner, just open nautilus in your home folder, go to VIEW --> SHOW HIDDEN FILES. 
and you might find something of use.
Unless someone happens to know what you're looking for, best bet would be to find the application's webpage/documentation.

---

### Post by F0rdPr3f3ct on 2006-04-17
[QUOTE=nalmeth]I'm sorry I don't know how to help you, but this doesn't appear to be a *begginer *question. [/QUOTE]

You are probably right. This not a beginner question. I'm also not new to linux. The only thing I wanted to know is, if there is a program which monitors another program for i/o.

tia, F0rd

---

### Post by stuporglue on 2006-04-17
Try lsof. It might have a LOT of output, so pipe it to a file...

lsof > ~/lsof_output

You might have to use sudo to run that command

sudo lsof > ~/lsof_output

View the file with your favorite text editor.

---

