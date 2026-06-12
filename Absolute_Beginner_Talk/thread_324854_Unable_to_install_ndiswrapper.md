---
title: "Unable to install ndiswrapper"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by Baethan on 2006-12-24
I'm back with another plea for help...
 
I've got Ubuntu 6.10 installed, and now I'm trying to connect to my wireless network. I understand that my wireless card is not supported, so I'm trying to install the ndiswrapper-util. (I'm relying heavily on the help pages within ubuntu.) The packages didn't show up in the Synaptic can't-remember-the-rest-of-the-name, so I went looking and found them on the CD that I installed Ubuntu from. When I tried to install one/any (with gdebi), I got an error saying "dependency is not satisfiable". I downloaded ndisgtk from Sam Pohlenz's blog, stuck it on a CD, and tried that, but got the same error message. (I believe the exact wording was "error: dependency is not satisfiable: ndiswrapper-utils") How can I get this working? I have no internet on the computer I'm working on; all other computers are inconveniently placed and run Windows. Thank you!

---

### Post by MkfIbK7a on 2006-12-24
Download ndiswrapper-utils-1.8_1.18-1ubuntu2_i386.deb and ndiswrapper-common_1.18-1ubuntu2_all.deb and libc6 

hope this helped

---

### Post by slagerst on 2007-03-17
I seem to be having a similar problem. I successfully installed 

[INDENT]ndiswrapper-utils-1.8_1.18-1ubuntu2_i386.deb

and 

ndiswrapper-common_1.18-1ubuntu2_all.deb[/INDENT]

but when i try to install

[INDENT]ndisgtk_0.5-1ubuntu1_all.deb

or

ndisgtk_0.6-0ubuntu1_all.deb[/INDENT]

i get the same "error: dependency is not satisfiable: ndiswrapper-utils" message.

I tried installing libc6 as per the previous advice, but it responds that I have a newer version already installed. what can i do? thanks so much!

---

