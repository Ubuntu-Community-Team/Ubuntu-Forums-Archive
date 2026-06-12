---
title: "Want to know if there is a program that can do this"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by Dapman01 on 2007-12-05
This is what I want to do
I am currently in collage, and I want to make backups even more secure.  What I want to know is if there is any way to leave one of my computers at home, always running, and be able to access it through the internet to store files/music/pictures, etc

I have two external hdd's but want to have a back up that is stored at home just in case I forget them

---

### Post by philinux on 2007-12-05
you need VNC.

Click on system>pref>remote desktop.

You'll have to search the forum too. I've never needed it.

---

### Post by saj0577 on 2007-12-05
> **Dapman01 said:**
> This is what I want to do
I am currently in collage, and I want to make backups even more secure.  What I want to know is if there is any way to leave one of my computers at home, always running, and be able to access it through the internet to store files/music/pictures, etc

I have two external hdd's but want to have a back up that is stored at home just in case I forget them

You mean access it as if you are sitting in front of it (VNC) or as a networked machine with shared folders?

Saj

---

### Post by rich.bradshaw on 2007-12-05
on home pc, 

sudo apt-get install openssh

then if you have a router, forward port 21 to the internal ip of that computer. (normally 192.168.1.something)

On home computer, go to [http://www.whatsmyip.org/](http://www.whatsmyip.org/) Ip at the top is your external IP.

On remote computer, if it's windows download [winscp]("http://winscp.net/eng/index.php"), linux you can just type your external ip.

Install winscp, fill in relevant info to connect. just use your normal linux username and password.

Dah dah - you can connect from anywhere in the world to your home pc and copy files around.

---

### Post by rich.bradshaw on 2007-12-05
VNC just lets you see the screen as if you are in front of your computer - my method lets you copy files as well.

---

### Post by asmiller-ke6seh on 2007-12-05
I agree - SSH is the way to go.

Also, you can use Simple Backup (SBACKUP) to automatically backup to the home system using the SSH setup. Neat and clean.

---

### Post by armware on 2007-12-05
i setup my media center pc for this. i use ssh and/or webmin, depending. just don't forget to forward ports on your router.

---

### Post by jfinkels on 2007-12-05
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by schorsch on 2007-12-05
.... VNC is not encrypted as far as I know ... so you will be more safe when using ssh ....

---

### Post by philinux on 2007-12-05
I learn something new everyday. What a forum eh. :)

---

