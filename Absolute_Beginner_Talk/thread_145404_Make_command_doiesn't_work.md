---
title: "Make command doiesn't work"
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by don cole on 2006-03-16
I have instructions 'type $ make' and it say command not found?

Now what?


Don Cole

---

### Post by Xian on 2006-03-16
You need a development package called build-essential:

$ sudo apt-get install build-essential

---

### Post by Sef on 2006-03-16
When adding a pacage, do this first:

sudo apt-get update

sudo apt-get install build-essentials


(replace build-essentials with other packages being installed.)

---

### Post by jam'ez on 2006-03-16
u did configure it first,
cd to directory then in terminal type
./configure

that configures it to then use the make command

---

### Post by don cole on 2006-03-16
Thanks all,

I forgot to mention I can't go online with Ubuntu.

That's why I need the make file to install a modem driver.

jam'ez when you say 'cd to directory' what directory?

Don Cole

---

### Post by henriquemaia on 2006-03-16
**cd** to the directory where you have the program you want to compile

---

### Post by jam'ez on 2006-03-16
i replyed to your private message. hope it helped.
Message i sent:

if it is a tar ball then extract the files. this will make a folder which is a directory, then go in to the directory. e.g.
if it is on the desktop and the extracted folder (directory) is called say modem then to get in the directory you do.

cd Desktop/modem

then do ./configure.
if you look in the extracted files you should see a file called README (a text file), should help you. may be called Install.

---

