---
title: "sudo apt-get install subversion doesn't work"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by omerb on 2008-02-11
Hi all,

I setup a brand new environment Ubuntu 7.10 and my first command is to install the subversion with

Code :
sudo apt-get install subversion

Here is the output.

omer@oldboy:~$ sudo apt-get install subversion
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package subversion
omer@oldboy:~$ 

I looked for subversion using synaptic but couldn't find it there too. I am sure I installed subversion on a brand new Ubuntu. does something change in ubuntu 7.10 ? 

Thanks in advance.

Note : 

In the sources.list file there are comments like

#Line commented out by installer because it failed to verify:

---

### Post by taurus on 2008-02-11
Look in System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and make sure you have enable all the sources there.

---

### Post by samb0057 on 2008-02-11
Edit /etc/apt/sources.list
There is a line in there that contains the worl "multiverse". Make sure it's not commented out.

---

### Post by drtre on 2008-02-11
make sure you've checked all the repos in Synaptic. check:
settings>repositories in the ubuntu software tab.

---

### Post by omerb on 2008-02-11
I changed "Download From" from TR to Main Server, and now it is working. 

Thanks.

---

