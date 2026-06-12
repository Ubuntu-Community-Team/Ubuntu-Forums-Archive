---
title: "Problem with aMsn and the Tls"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by raptor87 on 2007-07-11
Hello, I have installed amsn but I got a problem when I'm trying to open it. An error message appear asking me to download the TLS, because the program can't download by itself I decided to download the last version (1.5) from the net. 

I put it into a folder and I told to aMsn the folder where the TLS is, but aMsn continue to ask me to download the Tls. I also tried to download the version 1.4 but anything... aMsn doesn't work.

Can someone help me?

---

### Post by shearn89 on 2007-07-11
did you try installing amsn from synaptic? Go system -> administration -> Synaptic package manager and search for amsn. it should install all relevant files and should work fine, although i'm not certain if its the latest version.

---

### Post by raptor87 on 2007-07-11
No because I downloaded it from the official website of amsn, but I will try now ^^

---

### Post by raptor87 on 2007-07-12
I downloaded from synaptic, but it's the old version, and I like to download the new one ^^

---

### Post by kukibird1 on 2007-07-14
> **raptor87 said:**
> Hello, I have installed amsn but I got a problem when I'm trying to open it. An error message appear asking me to download the TLS, because the program can't download by itself I decided to download the last version (1.5) from the net. 

I put it into a folder and I told to aMsn the folder where the TLS is, but aMsn continue to ask me to download the Tls. I also tried to download the version 1.4 but anything... aMsn doesn't work.

Can someone help me?



Open a terminal and issue the following commands .

wget [http://internap.dl.sourceforge.net/sourceforge/amsn/tls-1.5.0-linux-x86.tar.gz](http://internap.dl.sourceforge.net/sourceforge/amsn/tls-1.5.0-linux-x86.tar.gz) 
tar xvzf tls-1.5.0-linux-x86.tar.gz 
sudo cp -f ~/tls1.50/* /usr/lib/tls1.50
Make sure /usr/lib/tls1.50 is set in the  tools>preferences>advanced options menu in Amsn. 
Restart Amsn

---

### Post by Free Penguin on 2007-07-15
look this: [www.freepenguin.it/tip8.html](www.freepenguin.it/tip8.html)

(it's in italian but I think you can easily understand)

Free Penguin

---

