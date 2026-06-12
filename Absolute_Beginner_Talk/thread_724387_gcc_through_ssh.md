---
title: "gcc through ssh"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by Damack on 2008-03-14
I can't seem to get any kind of C compiler to run on vista, but I can ssh to a linux server with gcc installed. Is there any way to use gcc on a file on my computer through ssh.

---

### Post by The Cog on 2008-03-14
Either copy all the sources up to the Linux server and compile them there, or perhaps log on to the Linux server and map a drive to a share un your desktop where the sources are.

Have you tried mingw - an open source compiler for windows?

---

### Post by Damack on 2008-03-14
Yeah. I've been trying to get it to work, but can't seem to figure it out. I'm not very good with computers. I installed it but can't seem to find any kind of executable.

---

### Post by ansicplusplus on 2008-03-14
Hy,
you could use sshfs to mount the directory of the file on your linux server. You just need an SFTP server for your vista machine.
But frankly I think it will be easier to get a c compiler running on vista.
Yours, ansicplusplus

---

### Post by Damack on 2008-03-14
Alright. Thanks. Any hints for getting MinGW to work?

---

