---
title: "apt-get wont work"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by zoidburg016 on 2006-11-19
I am trying to install build-essential, but apt-get won't work, I have tried it on other things and it wont work at all. It downloads the file then says
"dpkg: parse error, in file `/var/lib/dpkg/available' near line 2 package `checkinstall':
 value for `status' field not allowed in this context
E: Sub-process /usr/bin/dpkg returned an error code (2)
"
does anyone know how to fix this.

---

### Post by David Corrales on 2006-11-19
Maybe some corrupt packages/headers? Try running the following to see if it helps:
[B]sudo apt-get clean
sudo apt-get update[/B]
Then try to apt build-essential again.

---

### Post by zoidburg016 on 2006-11-19
It gave me the same error message.

---

### Post by zoidburg016 on 2006-11-19
I am trying to install build-essential, but apt-get won't work, I have tried it on other things and it wont work at all. It downloads the file then says
"dpkg: parse error, in file `/var/lib/dpkg/available' near line 2 package `checkinstall':
value for `status' field not allowed in this context
E: Sub-process /usr/bin/dpkg returned an error code (2)
"
I have already tried apt-get clean then apt-get update and I still get the same error. 
does anyone know how to fix this.

---

### Post by David Corrales on 2006-11-19
Hmm let's try to temporarily rename that file and see if it gets automatically build again. Type:
**sudo mv /var/lib/dpkg/available /var/lib/dpkg/avaiable-backup**
and then update your sources again **sudo apt-get update**

---

### Post by David Corrales on 2006-11-19
Keep your posts in one forum, they're easier to follow. I already posted a follow up on the original post.

---

### Post by aysiu on 2006-11-19
> **David Corrales said:**
> Keep your posts in one forum, they're easier to follow. I already posted a follow up on the original post.
I've merged the two threads.

---

### Post by zoidburg016 on 2006-11-19
Sory about making a second thread. I tried moving the file and it gave me a different error
"dpkg: failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory
E: Sub-process /usr/bin/dpkg returned an error code (2)
"

---

### Post by zoidburg016 on 2006-11-19
I opened the /var/lib/dpkg/avaible file and I noticed something strange, it had alot of @'s after the checkinstall package. I dont know if that has anything to do with it or not.

---

### Post by David Corrales on 2006-11-19
I just checked mine and it doesn't have any @. My output for **cat /var/lib/dpkg/available | grep checkinstall** is:
Section: checkinstall
Section: checkinstall
Section: checkinstall
Package: checkinstall
  Homepage: [http://asic-linux.com.mx/~izto/checkinstall/](http://asic-linux.com.mx/~izto/checkinstall/)
Section: checkinstall
Section: checkinstall
Section: checkinstall
Section: checkinstall

Btw: Thanks Aysiu :)

---

