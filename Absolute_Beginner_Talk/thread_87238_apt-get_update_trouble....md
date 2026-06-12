---
title: "apt-get update trouble..."
date: 2005-11-07
forum: Absolute Beginner Talk
---

### Post by grim918 on 2005-11-07
hello everyone. i just installed ubuntu and when i try to run apt-get update i get this message along with others:

W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)

can anyone help me out. I can't get any packages to install right now and i think its because i need to update the system but its just not working. thanks for any help you can give me.

---

### Post by Kyral on 2005-11-07
The Backports at Mirrormax don't exist anymore.

Replace that line with this one in your sources.list

deb [http://archive.ubuntu.com/](http://archive.ubuntu.com/) ubuntu hoary-backports

(I think thats it)

---

### Post by tonysathre on 2005-11-07
try browsing to the mirror to see if it is down, also post your sources.list

---

### Post by Kyral on 2005-11-07
Mirrormax is shutdown for HoaryBackports. Its going to be down ;P

Its on Archive.Ubuntu.com now

---

### Post by tonysathre on 2005-11-07
sweet, didnt know that

---

