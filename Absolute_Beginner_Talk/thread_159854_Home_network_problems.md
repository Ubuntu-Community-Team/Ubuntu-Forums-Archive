---
title: "Home network problems"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by Amorphous_Snake on 2006-04-13
I have 2 PCs, one with Windows and the other with Ubuntu. I have them connected and I am sharing my internet connection from my Windows PC smoothly. I manually configured the IPs in both PCs to 192.168.0.1 and .2.

But I have a problem with the shared folders. Ubuntu says "Can't display contents of this folder". Although I could access the shared folders before configuring the internet connection. I selected a folder in Ubuntu to be shared in Windows using Samba (SMB). On the Windows PC, I get asked about a password, I enter my Ubuntu password and I get asked again!

Help!

---

### Post by echo $USER on 2006-04-13
When you try to connect to a share on your Ubuntu box from your M$ box, it will prompt you for your Samba user/passwd.  [Look at this]("http://easylinux.info/wiki/Ubuntu#How_to_add.2Fedit.2Fdelete_network_users") to see how to add Samba users and passwd.

As far as your trouble connecting to a shared folder on you M$ box, there shouldn't be any problem.

---

### Post by indytim on 2006-04-13
Having gone through the network challenges recently, additional thing to check,  (if you haven't already), check you firewall(s).  Make sure everything is "happy" between the two boxes... took me awhile to figure that one out....](*,) 

IndyTim

---

### Post by djsroknrol on 2006-04-13
what's your xorg.conf like?...is it set to "share"? solved all my problems at once on my first install..

---

