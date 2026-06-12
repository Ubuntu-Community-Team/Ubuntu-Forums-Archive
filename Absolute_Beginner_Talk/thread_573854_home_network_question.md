---
title: "home network question"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by tonymoloney on 2007-10-12
I'm really getting into ubuntu. I now have kubuntu installed on my Lenovo laptop (as the ONLY OS) and xubuntu installed on an old desktop, dual-booting (or is that thrice booting?) with DreamLinux and Window$ 2000
The two computers are connected to the Internet and I hope, each other, via a Linksys 5-port switch.
I can surf the net from either computer, but when I look at the network, I can only see the computer that I am currently working on.
Is there a tutorial anywhere that will show me how to set up a local area network so that I see one computer from the other, and maybe share files?
I did a search but couldn't find what I was looking for (like trying to look up a word in a dictionary when you don't know how to spell it)

---

### Post by zek725 on 2007-10-12
Ubuntu:Feisty [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)
Kubuntu Feisty [http://kubuntuguide.org/Feisty](http://kubuntuguide.org/Feisty)
Xubuntu Feisty [http://xubuntuguide.org/](http://xubuntuguide.org/)

---

### Post by Schinoble on 2007-10-12
have a look into samba 

set up samba on both conputers, and share folders with it 

than on one computer through samba point to the ip address of the other computer and you shuold be able to see the shared folders

if you want to share the windows drives too you might wanna get sudo apt-get install ntfs-config than run it from your desktop to enable read-writing on the win partition

---

### Post by drinkpepsi on 2007-10-12
[http://www.reallylinux.com/docs/sambaserver.shtml](http://www.reallylinux.com/docs/sambaserver.shtml)

---

