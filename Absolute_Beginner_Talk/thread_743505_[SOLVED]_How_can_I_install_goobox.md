---
title: "[SOLVED] How can I install goobox?"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by sdim on 2008-04-02
Could someone help before I go crazy?
I've downloaded Goobox tarball and decompressed it on the Desktop.
What should I do to install it?
I follow the instructions,but I can't get past the "./configure" command.

Thanks.

---

### Post by Crafty Kisses on 2008-04-02
> **sdim said:**
> Could someone help before I go crazy?
I've downloaded Goobox tarball and decompressed it on the Desktop.
What should I do to install it?
I follow the instructions,but I can't get past the "./configure" command.

Thanks.
Well, what happens after the **./configure** command?

---

### Post by smartboyathome on 2008-04-02
cd to the directory (cd ~/Desktop/foldername) in a terminal and then run ./configure. Make sure you have build-essential installed, and any missing dependancies have to have the -dev files installed.

---

### Post by meborc on 2008-04-02
this long, but good guide will help you in the future... 

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

basically explains everything about how to install anything in ubuntu

---

### Post by sdim on 2008-04-02
Thanks for answering.
I've created a Goobox directory,and put all the contents of the application inside.
I type "cd Goobox",which takes me to this directory,and when I type "./configure",it says "no such file or directory".
Yes,I have installed Buildessential,etc.

---

### Post by meborc on 2008-04-02
> **sdim said:**
> Thanks for answering.
I've created a Goobox directory,and put all the contents of the application inside.
I type "cd Goobox",which takes me to this directory,and when I type "./configure",it says "no such file or directory".
Yes,I have installed Buildessential,etc.

maybe you do not have to install it... is there an executable inside the folder? or a INSTALL or README text file?

---

### Post by smartboyathome on 2008-04-02
By the way, Goobox is in the repos.

---

### Post by sdim on 2008-04-02
I just would like to learn how to install tarballs,so that's why I'm trying.
I'm sure it must be in the repos...

---

