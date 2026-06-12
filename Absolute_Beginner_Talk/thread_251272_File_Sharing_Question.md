---
title: "File Sharing Question"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by thornomad on 2006-09-05
Hi,

I have a Ubuntu Server (command prompt only) installed at home and Ubuntu Desktop edition on one of my laptops.  

What is the easiest way to setup file sharing between my two systems? 

On my Mac laptop I use AFP (have installed Netatalk on the linux server) and allowed port 548 on my router to be forwarded to the server; this allows me access to my home folder with a username and password -- which is all I need.  Though I sometimes am without my Mac laptop and only have my Linux laptop, so:

What is the correct sharing system to use Linux to Linux ?  And what port should I forward ?

Thanks,
Damon

---

### Post by whizbaby on 2006-09-05
You're looking for NFS (don't know the port, though. Anybody else?)

---

### Post by thornomad on 2006-09-05
Is NFS enabled by default on the server ?  With AFS I had to install Netatalk (which was amazingly easy -- "thanks linux!").

And, I guess: is it pretty secure ?  I am over paranoid (I don't even have anything that needs to be protected on my system!).

---

### Post by Bagnaj97 on 2006-09-05
I use samba for file sharing as it works with Mac, windows and linux. To share folders with samba you need to install the samba packages from the repositories.

---

### Post by petri on 2006-09-05
Maybe [SSH]("http://users.bigpond.net.au/hermanzone/p11.htm") is something for you? 

NFS [HOWTO]("http://nfs.sourceforge.net/nfs-howto/index.html") yu find here. Lots of text but it's still quick ;) 

I use NFS but I don't have a laptop and no need to contact server from outside world :cool:

---

### Post by thornomad on 2006-09-05
I use SSH currently for the command prompt ... oh!  Can I connect to send files that way too ... (fiddling around in Linux -- comes back) ... I can!  Terrific.  Well, I just need to find the port number for SSH and that is good enough for me -- I need to access the command prompt anyway so this will kill two birds with one stone.


Thanks everyone!

Damon

---

### Post by omns on 2006-09-05
.

---

