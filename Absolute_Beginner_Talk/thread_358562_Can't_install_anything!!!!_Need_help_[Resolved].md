---
title: "Can't install anything!!!! Need help [Resolved]"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by guna_k on 2007-02-11
I just installed my ubuntu 6.10.  But it is completely unusable for the applications I want. Here is my experience trying to install any usable package:

- Java JDK: 
I wanted to use the latest jdk to I downloaded the rpm (since that was the option for linux)
I was trying install an rpm package and I can't. When I read the forums they said I should use alien. So i tried downloading alien from here:
[http://packages.ubuntu.com/hoary/admin/alien](http://packages.ubuntu.com/hoary/admin/alien)
The installer complains saying it need debhelper (dependency missing). So I tried installing debhelper. Then it failed saying missing dependency for text2html (can't remember maybe it was html2text). 
This is driving me crazy how do I install any package on ubuntu?? Am I expected to traverse to the complete tree of dependencies by manually going to each package page and installing it.
I tried typing on shell:
 $sudo apt-get install alien
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package alien

- I tried installing emacs 
I downloaded the source and I try:
$./configure 
loading cache ./config.cache
checking host system type... i686-pc-linux-gnulibc1
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.
Why is gcc missing? When I try which gcc, it shows gcc.
$which gcc
$/usr/bin/gcc


Thanks

---

### Post by taurus on 2007-02-11
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by teaker1s on 2007-02-11
sounds like your sources list also needs the universe/multiverse repositories uncommented

---

### Post by aysiu on 2007-02-11
> **taurus said:**
> [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
And this:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by Maestro23 on 2007-02-11
Slow down and take a deep breath. You are trying to run before you walk.:) 

Some links that will help you:

How-To Install: [http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
                             [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Enabling Extra Repositories: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

You will need to update your repositories in /etc/apt/sources.list to get the programs you are looking for.  Follow the instructions on the link I gave you(Enabling Extra Repositories).

Once you do that, you will be able to get java6 via Synaptic(GUI) or sudo apt-get(command line).

---

### Post by guna_k on 2007-02-11
Thanks a lot for all the information!
 I will readup on all that. And hopefully I will be good to go after that.

---

### Post by guna_k on 2007-02-17
Ubuntu is the coolest! I could install all the stuff I wanted through aptitude. 
"aptitude" rocks!

---

