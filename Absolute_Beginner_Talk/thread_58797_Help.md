---
title: "Help"
date: 2005-08-21
forum: Absolute Beginner Talk
---

### Post by evansa4 on 2005-08-21
Hi guys i am new to linuxs and have no info about i need some help with installing so progams 


flash 

and does linux need antivirus

also were can i get msnm from thanks

---

### Post by Qrk on 2005-08-21
A good place to find instructions for Flash and other non-free formats is [www.ubuntuguide.org](www.ubuntuguide.org) It isn't too hard, and the guide has a great intro for the command line. 
As far as antivirus, Linux doesn't really need it, but a lot of people have it on Linux if they dual boot to clean windows drives. 
Microsoft doesn't make MSN for linux (small wonder), but Ubuntu comes with Gaim,  a free multi client IM, which works with MSN. Its under applications > internet. The problem is sometimes you'll be kicked off the MSN network. If this happens its easy enough to login again.

---

### Post by evansa4 on 2005-08-21
o thanks i only have this linuxs and wont need it thanks v much

---

### Post by evansa4 on 2005-08-21
Help again about that webpage u give me i do not understarnd is there a easyer way to install progams thanks

---

### Post by sapo on 2005-08-21
[QUOTE=evansa4]Help again about that webpage u give me i do not understarnd is there a easyer way to install progams thanks[/QUOTE]

If you mean "easier" talking about installer wich you just click> next next next finish you answer is NO, you dont have a easier way.

Take you time to learn about apt-get and synaptic.

Click on System -> Administration -> Synaptic Package Manager

You just have to select the software you want to install and then click in Apply.

Btw.. [www.ubuntuguide.org](www.ubuntuguide.org) is the easiest guide out there.. but it uses command line cause its easier to share and it works in all kinds of config...

in no time you will see that is easier to install apps using the command line and apt-get, you just need to get used to it ok?  :grin:

---

### Post by evansa4 on 2005-08-21
ok i get that but what about the software i downloaded how do install that

---

### Post by TristanMike on 2005-08-21
Most of the software you can ever need is located in the repositories [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) and you can install via apt-get/synaptic as sapo has said. Just do a search in Synapic Package Manager for what your looking for, click the box, click apply and poof, it takes care of everything for you.

Is there any program you're thinking about in particular?

---

### Post by sapo on 2005-08-21
[QUOTE=evansa4]ok i get that but what about the software i downloaded how do install that[/QUOTE]

it depends of what kind of software you have downloaded...

if its a .deb you need to run:

```
dpkg -i package.deb
```

if its a .run

```
chmod +x package.run
./package.run
```

if it is a tar.gz

```
tar xzvf package.tar.gz
```

if it is a tar.bz2

```
tar xjvf package.tar.bz2
```

for the last two you SHOUL READ the README file or the INSTALL file..

But usually after unpacking you have to enter the folder that the tar command created.. and run ./configure, make, make install.. like this:

```
cd package
./configure
make
sudo make install
```

---

### Post by evansa4 on 2005-08-21
ok try that i think i installed some thing and with the download i did what it said but no luck hope i do it or i will go back to xp

---

### Post by evansa4 on 2005-08-21
Ok tryed everything no luck installing downloads please help

will some 1 go step bye step with me please

---

