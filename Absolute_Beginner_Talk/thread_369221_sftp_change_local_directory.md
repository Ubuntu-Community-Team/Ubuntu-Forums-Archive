---
title: "sftp change local directory"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by uberdrah on 2007-02-24
Hi,

Another very simple question.

When using ssh to login into my ubuntu box from my windows machine i want to use sftp to transfer file to the windows machine.

My remote directory is

sftp> pwd
Remote working directory: /home/drah

and the local directory is 

sftp> lpwd
Local working directory: /home/drah

How do i change the local working directory to be the windows machine?

Thanks

Rich

---

### Post by nereid on 2007-02-24
My guess would be *lcd /path/of/local/directory*.

---

### Post by uberdrah on 2007-02-24
I've tried that but the local directory is on the same machine as the remote directory when i login and i want to change it from the linux machine to the windows machine.

remote directory is

sftp> pwd
Remote working directory: /home/drah

local directory is

sftp> lpwd
Local working directory: /home/drah

i want to local to directory to be  

c:\ftp

on the windows machine

Thanks

---

### Post by nereid on 2007-02-24
Are they really the same directories? Does a ls and a lls reveal the same files?

---

### Post by uberdrah on 2007-02-24
Yeah they are the same directories as you can see they are the directories that i get when i login

drah@darwin:~$ sftp drah@darwin
Connecting to darwin...
drah@darwin's password:
sftp> ls
Desktop   Examples
sftp> lls
Desktop  Examples

I haven't changed anything in the ssh config file would i need to do something there?

Thanks

---

### Post by nereid on 2007-02-24
Wait a second what are you trying to do? Connect via sftp from Windows to Ubuntu? Is your shh daemon activated in Ubuntu? And if you try to connect from your Ubuntu system via sftp on your Ubuntu system then it is no wonder why you can't access c:\ftp.

Which kind of sftp program do you use on Windows? I would recommend [psftp](http://www.putty.nl/latest/x86/psftp.exe).

---

### Post by uberdrah on 2007-02-24
Thank you very Nereid.
Its so obvious when you put it like that, i think my head is on overload this week trying to asorb all the linux stuff i have read.

---

