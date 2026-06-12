---
title: "How To Install NVU"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by buzlink on 2006-09-19
I have a NVU install package sitting on my desktop, but can't seem to get the program to install.  I can extract the package to my desktop folder and run the program, but can't get it to install into usr/lib/ dir.  I keep getting a permission error. I'm assuming I have to be logged in as root to perform this action but not sure how to do so.

Thanks!

NVU Install package file name nvu-1.0-pc-linux2.6.10-gnu.tar.bz2

---

### Post by DarkN00b on 2006-09-19
I installed NVU through Synaptic Package Manager.  It works really well for me.

---

### Post by jd65pl on 2006-09-19
Try finding NVU in Synaptic it is in there and it will save you all the trouble of compling it for yourself.

J

---

### Post by hassan_saeed on 2006-09-19
I installed AUTOMATIX from their website. and it installed for me not only the nvu but also Anjuta and Bluefish. 

Automatix is a must have if you want to feel empowered with ubuntu. 

but not knowing automatix for a long time did me a great advantage becasue i learnt the things the hard way ;)

---

### Post by jd65pl on 2006-09-19
Automatix is good for the initial setup of a computer e.g. to get restricted format codecs etc. But learning to use synaptic or even "add/remove programs" is definately a good idea

---

### Post by macdo on 2006-09-19
Here are generic installation instructions from source. Usually, however, the tarball will have a file called README that will give you the exact instructions. 
Before you try this, make sure you have got the package called build-essentials: ```
sudo apt-get install build-essentials
```
Untar the file you have on your desktop to a folder somewhere.
Then, in a console, cd to that folder: ```
cd /home/user/nvuuntarred
```
Then run as root the three commands:```
./configure
make
make install
```

Now for the easy way, which will give you the ubuntu package (just as recent as the tarball you've got):
```
sudo apt-get install nvu
```

---

### Post by undertherift on 2006-09-19
The three steps that Macdo mentioned
```

./configure
make
make install

```

are the key to installing things from source. 

From my experience, i've found that after you run the ./configure command, there will be a file created in that same directory, called a Makefile.  This Makefile is the key to the install.  It is  usually well labeled - it will tell you how to change the path for the install or what modifications you can make.  Often times, there is also a ReadMe or Install guide in this directory.  It *should* tell you how to go about it.  

Keep in mind, this will not really download/install dependencies, so when you're 90% done with your install and it fails because of a depdency thing, you get into a computer-breaking mood.](*,)   (trust me, i know).  So i suggest going via synaptic or apt.  

response to the root thing: if you just put "sudo" before your statement you will run it as root. ie,
```
sudo apt-get install nvu
```

Hope that helps. I'd try some of this so that i can be more specific, but i'm at work, and my box is off at home. Sorry!

-Vik:-\"

---

### Post by Brunellus on 2006-09-19
there is ZERO need to go through all the compilation steps if you have no compelling reasons to go with the latest build of NVU.  It's already in the repositories. 

First, ensure you've added the 'universe' and 'multiverse' repositories:

[http://monkeyblog.org/ubuntu/installing.html#enabling_extra_repositories](http://monkeyblog.org/ubuntu/installing.html#enabling_extra_repositories)

Then install, using the Synaptic package manager:

[http://monkeyblog.org/ubuntu/installing.html#installing_with_synaptic](http://monkeyblog.org/ubuntu/installing.html#installing_with_synaptic)

---

### Post by buzlink on 2006-09-19
> **DarkN00b said:**
> I installed NVU through Synaptic Package Manager.  It works really well for me.
That is what I ended up doing!
Thanks

---

### Post by Carnivorum on 2007-12-28
> **DarkN00b said:**
> I installed NVU through Synaptic Package Manager.  It works really well for me.

Bs'd

I can't find NVU in the Synaptic Package Manager.  Where should I look for it?


Eliyahu

---

### Post by Carnivorum on 2007-12-28
Bs'd

I downloaded NVU for Linux, but I can't get it installed. 

How do I install it?


Eliyahu

---

### Post by rugglesworth on 2007-12-28
Just open a terminal and type:

sudo apt-get install kompozer

Apparently NVU goes by a different name nowadays, but all the functions are the same.

---

### Post by Carnivorum on 2007-12-28
Bs'd

It works!

Thanks for the help!


Eliyahu

---

