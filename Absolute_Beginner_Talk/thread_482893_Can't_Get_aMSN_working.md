---
title: "Can't Get aMSN working"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by ronisc on 2007-06-24
Hi all

I am using ubuntu feisty.
trying to work with aMSN. 

First I tryed with my pc.I installed the program.
When I am trying to conectt a window pups up and telling me to install TLS (see pic1).
It's asking me to choose my system architecture.After choosing "Linux-x86" it's trying to bring "tls-1.5.0-linux-x86.tar.gz" from sourceforge, and it's not working. I am getting an error "Could't get http:// ...".(see pic2)

Anyway I was looking my synaptic and I saw tcltls and it is installed on my machine.

I tryed to install aMSN on my laptop and I am having the same problem.

Is anyone know how to get it work..... ???

Ronisc.

---

### Post by Gus_T_Reer on 2007-06-24
You don't say where you installed amsn from. I installed from Applications,Add/Remove Programs (version 0.96) and it installed all the dependencies (there were a lot) and worked straight away. Other tcl, tk dependencies other than tcltls include tcl8.4, tk8.4.
Full list of dependencies say:
imlib11
tcl8.4
sox
tk8.4
libpng12-0
docker
tcltls
python
libc6
libgcc1
libice6
libjpeg62
libsm6
libstdc++6
libx11-6
zliblg

---

### Post by ronisc on 2007-06-24
I have Install aMSN from synaptic. I am sure it took the relevant dependencies.
On my laptop I tryed to install from automatix2, but I hade the same problem from there.

I have install sepertly tcl8.4.
by the way I have versions 8.5 and 8.3 install aswell.

---

### Post by Gus_T_Reer on 2007-06-24
That's mighty strange, getting the same thing on 2 different machines by installing using different methods.

Firstly, in both cases it would appear that tk/tls isn't installed properly before amsn is loaded, hence amsn trying to install it on the fly. It could be that if you're running amsn as your user rather than root then the system won't install tls and this is creating the error message. I have to emphasise that this is pure guesswork.

If I was in your situation I would uninstall amsn the same way I installed it and then attempt to install it the way I did above. This worked for me.

---

### Post by Crafty Kisses on 2007-06-24
> **ronisc said:**
> Hi all

I am using ubuntu feisty.
trying to work with aMSN. 

First I tryed with my pc.I installed the program.
When I am trying to conectt a window pups up and telling me to install TLS (see pic1).
It's asking me to choose my system architecture.After choosing "Linux-x86" it's trying to bring "tls-1.5.0-linux-x86.tar.gz" from sourceforge, and it's not working. I am getting an error "Could't get http:// ...".(see pic2)

Anyway I was looking my synaptic and I saw tcltls and it is installed on my machine.

I tryed to install aMSN on my laptop and I am having the same problem.

Is anyone know how to get it work..... ???

Ronisc.
That's what happened to me too, I installed it through Automatix, then I uninstalled it and reinstalled it using the terminal and it worked fine.

---

### Post by arnieboy on 2007-06-24
> **ronisc said:**
> Hi all

I am using ubuntu feisty.
trying to work with aMSN. 

First I tryed with my pc.I installed the program.
When I am trying to conectt a window pups up and telling me to install TLS (see pic1).
It's asking me to choose my system architecture.After choosing "Linux-x86" it's trying to bring "tls-1.5.0-linux-x86.tar.gz" from sourceforge, and it's not working. I am getting an error "Could't get http:// ...".(see pic2)

Anyway I was looking my synaptic and I saw tcltls and it is installed on my machine.

I tryed to install aMSN on my laptop and I am having the same problem.

Is anyone know how to get it work..... ???

Ronisc.
do the following in terminal:
```
wget http://internap.dl.sourceforge.net/sourceforge/amsn/tls-1.5.0-linux-x86.tar.gz
```
```
tar xvzf tls-1.5.0-linux-x86.tar.gz
```
```
sudo cp -f ~/tls1.50/* /usr/lib/tls1.50/
```
restart amsn

---

### Post by ronisc on 2007-06-25
THANX arnieboy!!!!!

It is working now.
I guess that there are some installation problem....
 but anyway it is working now.

ronisc.

---

### Post by uxe1 on 2007-06-30
thanx  i was having the same problem. im just wondering if someone can explain what all that means?

---

### Post by Belgatom on 2007-07-03
Nice one. Had the same problem. Now I don't have that problem anymore. 

Just another question. I am working on a rather small laptop (12inch screen) and in the main window of amsn, where you can read all your online buddies, there is an Amsn logo on the background. Now, because of the small screen, this makes it harder to read the names online. Is there anyway to make this white or plain coloured?

---

### Post by vivia on 2007-07-04
Belgatom: If you mean the aMSN logo at the BOTTOM of the contact list, you can disable it on Preferences -> Advanced -> Show aMSN banner (near the top). Otherwise, can you send a screenshot?

---

### Post by Belgatom on 2007-07-06
[Screenshot]("http://users.telenet.be/belgatom/ubuntu/amsn.png")

The Logo of Amsn is behind my contacts which I would just like to see blank.

---

