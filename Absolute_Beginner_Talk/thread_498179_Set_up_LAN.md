---
title: "Set up LAN"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by Bhargavi on 2007-07-11
bnf

---

### Post by Bhargavi on 2007-07-11
can anybody suggest me how do i setup LAN on my machine
pl. give step by step procedure as i am new to this.

Thanx in advance

---

### Post by Bhargavi on 2007-07-11
can anybody suggest me how do i setup LAN on my machine
pl. give step by step procedure as i am new to this.

Thanx in advance

---

### Post by pebo on 2007-07-11
You could try [samba]("https://help.ubuntu.com/community/ComprehensiveSambaGuide?highlight=%28samba%29") for networking with windows or [nfs]("https://help.ubuntu.com/community/SettingUpNFSHowTo?highlight=%28nfs%29") if only networking linux machines.
HTH

---

### Post by Bhargavi on 2007-07-11
I found out the answer.
u need to go to System ->Administration -> n/w tools
select the n/w device to Ethernet interface click configure.
Enter your password.
Configuration -> static ip address
ip address -> ur s/m ip address
subnet mask -> 255.255.255.0
click ok
you established lan connection
thats done

---

