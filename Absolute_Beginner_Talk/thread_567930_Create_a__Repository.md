---
title: "Create a  Repository"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by ammar_shahraki on 2007-10-05
My internet connection is very slow. **How I can create a repository in a folder from .deb files?**

You can do this in Fedora7 with copy .rpm files to a directory and use a simple command such as **"createrepo" ?!**. but this command dos not exist in ubuntu

---

### Post by mike555 on 2007-10-05
You could go to one of your friends that have high speed connection and  using the live CD on their computer download the deb files and save them to a thumb drive , (I think, I've not tried it ) ....... or if you have a laptop you could go to your local hot spot , like a library  and get them ......

---

### Post by mali2297 on 2007-10-05
I don't know, but this might help:

[https://help.ubuntu.com/community/SynapticOffline](https://help.ubuntu.com/community/SynapticOffline)

---

### Post by Joe Dinmore on 2007-10-09
Not quite what you're asking for, but maybe you could look at AptonCD
aptoncd.sourceforge.net/

---

### Post by jars99 on 2008-02-07
apt-mirror will do it
 sudo apt-get install apt-mirror
then modify /etc/apt/mirror.list to your needs

---

