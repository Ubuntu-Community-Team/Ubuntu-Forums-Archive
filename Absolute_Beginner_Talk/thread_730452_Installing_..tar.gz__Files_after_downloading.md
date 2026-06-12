---
title: "Installing ..tar.gz  Files after downloading"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by SILLAT on 2008-03-20
Hey i need some help installing Tar.gz files . .
I've been reading so much sites an forums all nite an i still don't fully understand how to install my file Tar.gv file from downlods all now :confused:
i'm trying to install the new CLAMAV antivirus 92.1

i have done the  sudo tar -xvzf /home/john/Desktop/clamav-0.92.1.tar.gz part and i'm stuck right there, can someone break down the rest by telling me what to type in the terminal from here. and how to get it install and working ..

i really dont need no more links to sites tht hav tar.gz file help, i've had e-nuff... i jus need ur help !

---

### Post by forrestcupp on 2008-03-20
Well, you should give us a link to the instructions you're following, and we'll help you.  There are different ways to install different programs.

---

### Post by Sockerdrickan on 2008-03-20
.tar.gz is like zip, not an exe installer and you shouldn't use sudo when you don't need to.
cd into the dir if it untar'd one or else you have your binary which you can ./exec

---

### Post by SILLAT on 2008-03-20
i dont remember exactly where i saw it .. ive been aroun almost all ubuntu pages/forums
do u hav a beter way to install the tar.gz file from clamav 92.1

---

### Post by wormser on 2008-03-20
You should install programs from System> Administration> Synaptic Package Manager.   Clamtk is the graphical front for clamav and is in the repository.

---

### Post by forrestcupp on 2008-03-21
> **SILLAT said:**
> i dont remember exactly where i saw it .. ive been aroun almost all ubuntu pages/forums
do u hav a beter way to install the tar.gz file from clamav 92.1

Well, like wormser said, if clamav is in the repos, you really should install it that way.  It just makes everything a lot easier, especially if you ever want to uninstall it.

And like Tux0r said, tar.bz is just a compressed file, like zip.  It's possible to put anything in a tar.bz just like you could put anything in a zip file.  That's why there's not just one answer on how to install every tar.bz.  Some of them are just the binary and data files, you just extract them into their own directory and run the binary to run the program.  Some of them are python files that have their own way to install.  A lot of them are C source code.  You just never know.  Your best bet is to extract the tar.bz to a directory in /home somewhere and read the Readme file to see what it says.

Having cleared that up, if you're insistent on installing clamav this way instead of with the repository version, I checked it out, and it *is* source code that needs to be compiled.  [Here](http://www.psychocats.net/ubuntu/installingsoftware#source) is a good guide for compiling programs from source.  In this guide, which is by aysiu, I would change everywhere it says **aptitude** to **apt-get**.  I believe that now, aysiu would tell you the same thing.

---

