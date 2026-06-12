---
title: "SSH mess"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by duveit on 2006-09-08
I got a computer on a network which I cant reach directly, however I can enter it from another computer on the network using SSH.

So what I want is some files from a computer on the network to my computer or the server on the network.

Connection is like this 

[My comp]--SSH>[server]--SSH>[the machine with files]

So.. is there something like "wget" that I could use from the server machine to get files from the secondary machine? Or is there someway I can have access to both the server files and the computer I'm in a SSH session with while connected?

And does this make sense.. I hope so.

Help greatly appriciated!

---

### Post by infoburner on 2006-09-08
peice of cake. just ssh into the first machine, then do 
```

sftp *second machine*

```
sftp is a ftp program that works through ssh. so in sftp, you just cd to the directory with the files you want, then type
```

get *filename*

```
and the file will be copied to the first machine.

---

### Post by darrenm on 2006-09-08
also scp

```
scp file user@ip.address:file
```
or
```
scp user@ip.address:file file
```

or have a look at sshfs, 
```
sudo apt-get install sshfs
```
```
sudo shfsmount user@ip.address:folder mount/point
```

---

### Post by duveit on 2006-09-08
Thanks, sftp worked like a charm!

I'm sure scp would aswell, I will have to check it out.

---

