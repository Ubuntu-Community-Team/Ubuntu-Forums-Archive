---
title: "[SOLVED] Networking using NFS"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by IanB2 on 2007-10-12
I've managed to set up samba and can share files between linux PCs using the SMB shares.

I would prefer to use the NFS shares instead. I've set up shares in the same way and have used the 'Connect to server' tool selecting SSH using static IP addresses. I can mount the shares from either PC but always get the 'Couldn't display "ssh://ian@192.168.0.6/home/ian/testl" "The attempt to log in failed."

Do you know what I'm doing wrong?

Is there a simple guide for 7.04 that shows you how to set up NFS shares without resorting to the 'terminal'?

---

### Post by IanB2 on 2007-10-13
The secret I've discovered is to install ssh. It is not part of the standard setup.

In the terminal **sudo apt-get install ssh**

All is working well and ssh looks really good!

---

### Post by llamakc on 2007-10-13
Congrats.

The package "ssh" is a metapackage that depends on and provides openssh-client [INSTALLED by DEFAULT] and openssh-server [NOT installed by default].

NFS can be useful too. Here is a group of links over at [http://wiki.ubuntu.com](http://wiki.ubuntu.com)

[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=NFS&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=NFS&titlesearch=Titles)

---

