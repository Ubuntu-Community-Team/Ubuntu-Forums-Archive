---
title: "network setup wizard?"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by iansane on 2007-09-22
Hi, another newb question.

In windows I didn't have to have a static IP to join 2 computers to the MSHOME work group and it only took 4 or 5 clicks of the mouse to do this. I can't find a setup wizard and don't want to install Samba if it's not necessary. I don't want to be a server. I just want to see other computers and share files, like in Windows where you go to My Network places and it's all there. Can I do something similar in Ubuntu or will I have to set my computer up as a server. And do I have to do that if both computers are running a linux distro? One is Ubuntustudio, the other is damn small linux, cause it only has 64M of RAM LOL

---

### Post by Pumalite on 2007-09-22
Sudo apt-get install open-ssh-server
(you will not be a server)

---

### Post by iansane on 2007-09-22
couldn't find package. Do I need to add a repository? I'll go google it.

---

### Post by iansane on 2007-09-22
found articles about open shh and open ssh. Are they the same thing? They both talk about  server and client.

---

### Post by Dr Small on 2007-09-22
```
sudo apt-get install openssh-server
```

Every ubuntu machine comes with openssh-client by default. You just need to install the server. Then open port 22 (using Firestarter), and then the clients can connect to the server.

Dr Small

---

### Post by iansane on 2007-09-22
thanks Dr. Small. hey, I just realized after looking in synaptic, I allredy have samba installed and the service is running too. Theres just nothing there in my network. I have a XP Home in the house that allready had a workgroup set up and files shared. They show up when I'm using my XP so should they also be showing up under "windows networks"? Or do I need to set the other XP differently?

---

### Post by Dr Small on 2007-09-22
Personally, I never fooled around to get the Windows PC's to show up on my Ubuntu. I just memorized their IP addresses, and use:
```
smb://IPADDRESS
``` and run it in nautilus to connect to that computer. But I am sure there is some way to get it to show up under "windows networks"...

Dr Small

---

### Post by iansane on 2007-09-22
hey cool that works through firefox too! Thanks!

---

### Post by Dr Small on 2007-09-22
I guess we both learned something new today :D
I never knew it worked in Firefox :p

Dr Small

---

### Post by iansane on 2007-09-22
I don't know if ssh has anything to do with samba, but after installing it, I also created a shared folder. In the process I named my domain/workgroup mshome. Now everything works perfect! Guess I found the network set up wizard. Just gotta figure out Damn Small Linux on my old junk computer now. I don't think I will drive you guys crazy with questions about that one cause it's gonna be a definite pain. That's why they got a DSL forum right?

---

### Post by Pumalite on 2007-09-22
I think you can install open-ssh-server there too.

---

