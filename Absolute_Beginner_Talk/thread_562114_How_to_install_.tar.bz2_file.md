---
title: "How to install .tar.bz2 file?"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by yangli on 2007-09-28
I am trying to install Rainlendar in my Feisty. 

I used the following commands (searched from web):

[B]unzip2 Rainlendar-Lite-2.2.tar.bz2
tar xf Rainlendar-Lite-2.2.tar
cd rainlendar2/
./configure[/B]

But ./configure gives me the following error messages:
**bash: ./configure: No such file or directory**

I can use some help here, thanks a lot in advance!

---

### Post by ryanVickers on 2007-09-28
Chances are this is just source code and it needs to be compiled.  Unfortunately, I know nothing about this :p

Edit: Just noticed something - make sure you type the **whole** path to the file/archive.  when you go "./configure", there's probably "no such file or directory" because your not in the right directory.  just make sure your in /something(probably /home/user/Desktop)/rainlendar2**/** and then run it.

---

### Post by s57nev on 2007-09-28
There is no need to compile make and make install this file. You just extract this folder and if you click on rainlendar2 file your callendar will be there. If you want to have your callendar there everytime you use Gnome just put it in System -> Sessions Add  link to your callendar there. Check this post: [http://www.howtogeek.com/howto/ubuntu/installing-rainlendar2-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/installing-rainlendar2-on-ubuntu/)

RTMF --> Read the manual first :) 

Have fun !!

---

### Post by Pumalite on 2007-09-28
sudo apt-get install build-essential

---

### Post by Malibu Illusion on 2007-09-28
No need to install build-essential; s57nev is correct.  You do not have to compile it; the error message you're getting means that there is no "configure" file because there doesn't need to be.

Also, for future reference, you can extract .tar.bz2 files with one command:

```
tar -jxvf file
```

Take care.

---

### Post by yangli on 2007-09-28
Thank you all.

---

### Post by stchman on 2007-09-28
> **yangli said:**
> I am trying to install Rainlendar in my Feisty. 

I used the following commands (searched from web):

[B]unzip2 Rainlendar-Lite-2.2.tar.bz2
tar xf Rainlendar-Lite-2.2.tar
cd rainlendar2/
./configure[/B]

But ./configure gives me the following error messages:
**bash: ./configure: No such file or directory**

I can use some help here, thanks a lot in advance!

.tar.bz2 is a bzipped tar archive.  To decompress that type of archive double click on it in Nautilus and File Roller will be able to decompress it.

To decompress this type of archive at the command line use the following:

```
 tar -xvjpf Rainlendar-Lite-2.2.tar.bz2
```

---

### Post by Perfect Storm on 2007-09-28
When you have decompressed the .bz2 file;

```
cd <into/the/decompressed/folder>
 ls -a
```

Please post the output.

---

