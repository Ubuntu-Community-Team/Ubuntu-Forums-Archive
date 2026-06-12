---
title: "How to use *.tar.gz"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by Cpitt77 on 2006-12-23
I am a complete beginner to Linux and I have been usine Windows almost exclusively scince I have owned a computer. I need to know how to run programs I download off the internet. More specifically, what do I do with a *.tar.gz file once I have downloaded it?

---

### Post by christopherberry11 on 2006-12-23
:KS Go to [http://monkeyblog.org/ubuntu/installing](http://monkeyblog.org/ubuntu/installing) - I found it a GREAT help!
Cheers

---

### Post by nikolaos on 2006-12-23
*.tar.gz is the equivalent of .zip  files on the Windows OS, you need to unzip them
```
tar -xvf filename.tar.gz
```
then you have a directory with the source code of the program you want to use.
You need to configure & compile that program for your machine.
To do that cd into the directory you created while untarring the tar.gz file and
```
./configure
make 
sudo make install  
```

be careful because ./configure might need some options enabled. It is better to read the INSTALL file (located in the untarred directory) before configuring.

---

### Post by steve.horsley on 2006-12-23
.tar.gz is like a windows .zip file. You can unzip it with the command:
**tar xzf filename.tar.gz**
or by right-clicking the file in nautilus (the file manager) and choosing Extract Here or Extract To.... What you do then depends on what the file contained. Typically it will either be some binary files that you can execute or some source code that you can compile.

Most stuff you are likely to need is in the repositories though.

---

### Post by xpod on 2006-12-23
Hi & welcome to the forums:D 

This place might help you out for installing stuff
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

but there are simpler ways when just starting out.
You can use synaptic which is in "system>admin>synaptic" and once you have the extra repositries enabled you`ll have access to over 20,000 odd apps at the click or 2 of a button.

Theres also "add/remove" in the applications menu which is like synaptics little brother.You can also access synaptic by clicking the "advanced" tab in add/remove

This is another great place to get you up & running.I cant give you any detailed help but there`s plenty who will if you have any questions

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

EDIT...beaten to it....

---

