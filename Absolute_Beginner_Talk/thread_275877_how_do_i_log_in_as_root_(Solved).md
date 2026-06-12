---
title: "how do i log in as root (Solved)"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by STREETURCHINE on 2006-10-12
](*,) i am trying to run adept,and install some more pakages but i have to loggin as root? i have itried su ,im told to enter password but i never put one there ,tried my log in password but that dont work.have tried sudogk that is a missing command .is there a way around the password as i have no idea what it is.

---

### Post by Iarwain ben-adar on 2006-10-12
Hi,
the normal way of doing such stuff is:
```
sudo aptitude install package_name
OR
gksudo synaptic
```

This would be the better way of doing such stuff ;)


Iarwain

---

### Post by pay on 2006-10-12
Ubuntu doesn't have a root account. Use sudo to gain root priveldges. sudo adept

---

### Post by petri on 2006-10-12
Do not **sudo adept**, please do **kdesu adept**. Groundrule is if you are trying to run a graphical application from CLI use **gksudo** in Ubuntu and **kdesu** in Kubuntu. More about graphical sudo here: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Why don't you just click the K-button and launch Adept? Then it prompts you to add your password and after that you got Adept with GUI.

---

### Post by STREETURCHINE on 2006-10-12
thanks for your help

---

