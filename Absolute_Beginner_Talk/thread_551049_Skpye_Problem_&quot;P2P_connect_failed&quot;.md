---
title: "Skpye Problem &quot;P2P connect failed&quot;"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by cybersaurabh on 2007-09-14
i have installed skype 1.4.0.99 using deb package provided at skype.com.
this version works fine under pclinuxos and xp on my pc.
but on ubuntu studio 7.04 it doesnt work.
whenever i try to sign in it gives error mesage of
"sign in failed : p2p connect failed"

please help me

---

### Post by xc3RnbFO8P on 2007-09-14
have you tried to reinstall skype?

---

### Post by cybersaurabh on 2007-09-14
yeah, it still didnt worked.

---

### Post by xc3RnbFO8P on 2007-09-14
Use Synaptic Package Manager, search Skype.
there should be to packages
Skype
Skype-static

---

### Post by cybersaurabh on 2007-09-14
no there is a single package of skype
i am using skype.com's repo for that

---

### Post by xc3RnbFO8P on 2007-09-15
I dont know if you have read this from Skype site:

Using Skype's apt repository

1. As the root user, add this line to the end of your /etc/apt/sources.list file:

deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

2. Then run apt-get update to sync to the latest repository and
apt-get install skype to install the latest version of Skype on your computer.

---

### Post by cybersaurabh on 2007-09-15
yes through this procedure i have installed latest skype
but now when i try to sign in it says p2p connect failed sign in failed
i am using skype behind a proxy server

---

### Post by xc3RnbFO8P on 2007-09-15
I hope you have all  information about your proxy server.

---

### Post by cybersaurabh on 2007-09-15
dude i know how to do proxy settings
i have done the same proceure as i did in pclinuxos and windows
in them it worked but in ubuntu it  is not working 
i dont know why ?

---

### Post by xc3RnbFO8P on 2007-09-17
Maybe you can use this from Skype forum site:

[http://forum.skype.com/index.php?showtopic=29679]("http://forum.skype.com/index.php?showtopic=29679")

[http://forum.skype.com/index.php?showtopic=90911&hl=p2p+connect+failed]("http://forum.skype.com/index.php?showtopic=90911&hl=p2p+connect+failed")

[http://forum.skype.com/index.php?showforum=18]("http://forum.skype.com/index.php?showforum=18")

---

