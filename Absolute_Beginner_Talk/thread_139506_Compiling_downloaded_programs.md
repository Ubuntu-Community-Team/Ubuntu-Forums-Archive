---
title: "Compiling downloaded programs"
date: 2006-03-04
forum: Absolute Beginner Talk
---

### Post by lyndon on 2006-03-04
I've been looking for an FTP client and have just downloaded gftp, which needs compiling. 

I tried running the ./configure command (I'm not entirely sure if I got the syntax right) but a response came back saying I had no suitable compiler in path $.

I then downloaded gcc 3.4 using

sudo apt-get gcc-3.4

which appeared to download and install successfully.

I then tried testing if it was there by typing

gcc -v

but got 

bash: gcc: command not found

What am I doing wrong?

Lyndon

---

### Post by soce_32 on 2006-03-04
You could do `sudo aptitude install gftp` and just start using it.  If you really want to compile things, install the build-essentials package.

If you want to try other ftp/sftp clients, do `sudo aptitude search ftp`.

---

### Post by Xian on 2006-03-04
Try adding this package set:

$ sudo apt-get build-essential  
[not essentials]

---

### Post by lyndon on 2006-03-04
[QUOTE=Xian]Try adding this package set:

$ sudo apt-get build-essential  
[not essentials][/QUOTE]

...for some reason, it didn't like it, and gave me:

lyndon@ubuntu:~$ sudo apt-get build-essential
E: Invalid operation build-essential

Do you think there might be something missing on my system? L

---

### Post by lyndon on 2006-03-04
[QUOTE=soce_32]You could do `sudo aptitude install gftp` and just start using it.  If you really want to compile things, install the build-essentials package.

If you want to try other ftp/sftp clients, do `sudo aptitude search ftp`.[/QUOTE]

Thanks very much - gftp looks very much like what I'm used to - the installation went fine. L

---

### Post by wthanna on 2006-03-04
sudo apt-get install build-essential

prior post left out the "install"

---

### Post by lyndon on 2006-03-04
[QUOTE=wthanna]sudo apt-get install build-essential

prior post left out the "install"[/QUOTE]

Got it - thanks so much - I shudder to think what one would have to pay Micro$oft for this level (and rapidity) of support!

I now wish that I hadn't spent £40 on WS_FTP Pro for Windows (a few weeks ago, when I'd heard of Linux but didn't know anything about it) - gftp does everything WS does.  L

---

