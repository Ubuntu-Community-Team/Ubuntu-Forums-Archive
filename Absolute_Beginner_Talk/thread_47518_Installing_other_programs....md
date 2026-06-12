---
title: "Installing other programs..."
date: 2005-07-08
forum: Absolute Beginner Talk
---

### Post by radbirts on 2005-07-08
I just started using Ubuntu today and I can't figure out how to install other programs. Can somone help me out? (sorry it's such a noob question)

---

### Post by poofyhairguy on 2005-07-09
[QUOTE=radbirts]I just started using Ubuntu today and I can't figure out how to install other programs. Can somone help me out? (sorry it's such a noob question)[/QUOTE]

NO problem. Thats a fine question. Your answer is synaptic. Thats how us Ubuntuers install most everything. To find this program go to "system" then "administration" then "synaptic package manager."

---

### Post by radbirts on 2005-07-09
What do I do in there? I'm really confused.

---

### Post by gammyhand on 2005-07-09
[QUOTE=radbirts]What do I do in there? I'm really confused.[/QUOTE]
 hehe, it can be confusing. I only started using linux a couple of weeks ago.

Basically what I do is load synaptic and then click search, then search for the package you want and then right click on the package you want to install and select mark for installation. Then just hit "apply". And bob's your uncle.

---

### Post by daageep on 2005-07-09
for synaptic, find an option where you can add or change repositories and add the universe repository. with the new repository, you will have access to more programs. search for the program you want. when you want to install a program, double click on it and you should see a checkmark, then click apply to install the program.

or you can use the command apt-get. open up a gnome-terminal. to search for programs, type "apt-cache search gnome" for example. that would display all results with the word gnome. usually this command displays way too many results. i usually use the grep command, for example "apt-cache search gnome | grep plugin". so lets say you found the right packages you want to install (lets say gnome123 or something), type "sudo apt-get install gnome123". this command will install the program and inform you on what else needs to be installed for the program to work (called dependencies). 

have fun =)

---

### Post by radbirts on 2005-07-09
I have one more question, I got XMMS installed but it won't do anything. It just freezes every time.

---

### Post by Kvark on 2005-07-09
[QUOTE=radbirts]I have one more question, I got XMMS installed but it won't do anything. It just freezes every time.[/QUOTE]

You need codecs. Open synaptic. Search for "codec". Click on the little box nex to the package called "w32codecs" to mark it for installation. Then click apply. That should solve the problem

---

### Post by gammyhand on 2005-07-10
[QUOTE=Kvark]You need codecs. Open synaptic. Search for "codec". Click on the little box nex to the package called "w32codecs" to mark it for installation. Then click apply. That should solve the problem[/QUOTE]
 A common bug with xmms (once you have the codecs installed) is that you need to change its output plugin to "esound" to hear anything.

---

