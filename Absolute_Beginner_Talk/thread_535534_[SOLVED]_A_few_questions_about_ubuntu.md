---
title: "[SOLVED] A few questions about ubuntu"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by chaoswings on 2007-08-26
Ok I'm totally new to linux I have a couple of questions. I'm basically the Windows guru going over to linux so I am a little lost

1) If I have linux does that mean I can run programs intended for UNIX?

2) are linux and UNIX the same thing?

3) Can I compile and run programs written in the C programming language or do I need VMware? 

4) Is it still recommended to have an antivirus and firewall on linux? If so what are the best ones.

5) Does Ubuntu Update take care of openoffice.org, firefox updates etc. or is it just for OS related updates?

6) How do I find out what version of ubuntu I am running?

7) what is the best IRC client for ubuntu? I want to be able to run XDCC bots and stuff

Well that's it... I managed to install ubuntu and dual boot it with vista. I also managed to force a larger resolution and a higher screen refresh rate as I was having problems with my nvidia card. So now I just need these last few things cleared up. 

(Been using ubuntu for about only 2 days now.)

---

### Post by finer recliner on 2007-08-26
1) most likely yes.
2) nope.
3) there are multiple free C compilers available for linux (cc and gcc for example)
4)more linux distros comes with a firewall call iptables. you do need an antivirus client. linux is generally more secure than windows and there are (almost) no virsuses made for linux
5) ubuntu updates your system when new packages are added to the offiial repository (package manager). this includes OOo and firefox.

---

### Post by finer recliner on 2007-08-26
6) run cat /etc/issue in a terminal

---

### Post by Steveway on 2007-08-26
Ok lets start.
1. + 2.Linux is no real Unix, it would propably become a license but since they would need to relicense it at every change to the kernel they don't do it. But you can run most if not all Unixprograms.
3. You sure can, Linux itself is written in C and a bunch of assemblercode.
4. There is a firewall built in called Iptables, the setup is good for normal Desktop use, but you should configure it to your needs if you intend to host a server.
You don't need antivirusprograms but you can install them to protect windowsusers so you won't send them some viruses by accident.
5. It takes care of everything you installed.
6. cat /etc/issue
7. There is no "best", the best is the one that fits your needs best. I use Xchat.
Have fun and welcome to the _free_ world.

EDIT: finer was faster than me.

---

### Post by very_japi on 2007-08-26
> 
1) If I have linux does that mean I can run programs intended for UNIX?
Well, at school i run all sorts of UNIX stuff on Ubuntu, so i'd say yes.

> 2) are linux and UNIX the same thing?
Linux is... more like Unix's grandchild. but you could say they're the same thing if you dont want to get all too strict and bury yourself in a hole of semantic bajadoo.

> 3) Can I compile and run programs written in the C programming language or do I need VMware?

You'll need some developer libraries in order to be able to compile, you can get them though synaptic or apt-get

> 4) Is it still recommended to have an antivirus and firewall on linux? If so what are the best ones.
Your chances of getting some virus in linux ar far smaller than Weendows, and there are some distros out there intended for the sole purpose of firewalling. But all in all, you are safer in linux without firewall or antivirus than you were in windows with firewall, antivirus, and anti-spy-ware.

> 
5) Does Ubuntu Update take care of openoffice.org, firefox updates etc. or is it just for OS related updates?
Yes,  indeed. And if it fails, firefox will update itself.

> 
6) How do I find out what version of ubuntu I am running?

System -> About Ubuntu

---

### Post by kknd on 2007-08-26
> **chaoswings said:**
> 
1) If I have linux does that mean I can run programs intended for UNIX?

If the program can be compiled under Linux, no problem.

> **chaoswings said:**
> 
2) are linux and UNIX the same thing?


No. Linux based O.S are inspired by UNIX, and in the creation, Linux was a free (as in freedon) replacement for UNIX.

> **chaoswings said:**
> 
3) Can I compile and run programs written in the C programming language or do I need VMware? 


Linux (and most of the applications) is made in C.

> **chaoswings said:**
> 
4) Is it still recommended to have an antivirus and firewall on linux? If so what are the best ones.


No need, there aren't malwares for Linux. If you really need a "firewall", you can do this with iptables.


> **chaoswings said:**
> 
5) Does Ubuntu Update take care of openoffice.org, firefox updates etc. or is it just for OS related updates?


After release, Ubuntu will take care of any security / bug update for any of his packages.

> **chaoswings said:**
> 
6) How do I find out what version of ubuntu I am running?


System -> About Ubuntu

> **chaoswings said:**
> 
7) what is the best IRC client for ubuntu? I want to be able to run XDCC bots and stuff


xchat rocks

---

### Post by sailor2001 on 2007-08-26
you can use gaim (pidgin) for multiple im...... amsn is msn clone and you can use cam and voice in that

---

### Post by chaoswings on 2007-08-26
Ok one last question

Regarding the C compilers and such.....

I took a look at gcc and there are a whole bunch of different ones...are they previous versions?

If they are previous versions which one do I install and also which libraries do I need to download (what are they called?) I'm new to C and linux so I'm twice as lost. I'm going to start taking C in college in about a week and I want my PC to be setup for it.

---

### Post by ddrichardson on 2007-08-26
> **chaoswings said:**
> Ok one last question

Regarding the C compilers and such.....

I took a look at gcc and there are a whole bunch of different ones...are they previous versions?

If they are previous versions which one do I install and also which libraries do I need to download (what are they called?) I'm new to C and linux so I'm twice as lost. I'm going to start taking C in college in about a week and I want my PC to be setup for it.

I'd check to see what C compiler your college uses first - they are mostly ANSI compliant but there are some differences. The last thing you want when struggling with some assignment on pointers and references is to  find out you couldn't get it working because you were using a different version to everyone else.

---

### Post by chaoswings on 2007-08-26
Thanks for the help, I guess I'll wait and see what they use as you suggest. 

That pretty much answers all my questions.

---

### Post by finer recliner on 2007-08-26
for the C compiler run:

sudo apt-get install build-essential

this will get you the latest C compiler so you can build programs from source.

---

