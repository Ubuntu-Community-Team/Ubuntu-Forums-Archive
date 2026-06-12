---
title: "Installing freeorion"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by snikkar on 2007-11-04
Hi,

I've been searching around for how to install freeorion. The only problem is that I dont know what they are talking about. It says the the game should be compiled. what is that and how do you do it? I have just downloaded freeorion but I dont know how to play it. Can someone please give a step by step guide to how to install freeorion using the terminal?

---

### Post by Maestro23 on 2007-11-04
> **snikkar said:**
> Hi,

I've been searching around for how to install freeorion. The only problem is that I dont know what they are talking about. It says the the game should be compiled. what is that and how do you do it? I have just downloaded freeorion but I dont know how to play it. Can someone please give a step by step guide to how to install freeorion using the terminal?

Is it a .tar file?  You will need to extract it 1st using the tar command.  Before that, you will need to install build-essential.

> sudo apt-get install build-essential

Read the following link on "Installing from Source": [http://www.psychocats.net/ubuntu/installingsoftware#source](http://www.psychocats.net/ubuntu/installingsoftware#source)

Once you extract the file to its folder, there should be a README/INSTALL document with instructions and what other programs it requires to run.  You must install these dependencies 1st before the game will successfully install.

*Installing from Source is not recommended for someone new to Linux, unless you just really have to.

Good luck.

---

