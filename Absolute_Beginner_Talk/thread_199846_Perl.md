---
title: "Perl"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by Nigge on 2006-06-19
Hi

I have a problem when I try to install *.PL files from for example [http://packages.ubuntu.com/dapper/allpackages](http://packages.ubuntu.com/dapper/allpackages)
In the root terminal i go into the archive, and write "perl *.PL" (* is the name), and then it tells me "Writing Makefile for xxxxxx" then I write "make", but then I get the message: "bash: make: command not found", what is the problem??

I'm a newbie, so please try to explain it, in a newbie-way :)

---

### Post by givré on 2006-06-19
They way you execute a perl file is good. So the problem is in the make thing.
What apps/soft do you want to install? Is there an INSTALL or a README in the archive? you should read it first.

---

### Post by Nigge on 2006-06-19
Yeah, there is, it tells me that I should write "make" :S

It is all kind of stuff, that you also can get on synaptic, but synaptic doesn't work for me in Ubuntu, only in Debian :S

I can't see what I am doing wrong, when I do what the readme tells me... :(

---

### Post by givré on 2006-06-19
Synaptic should work, i think you should try to get it working instead of compiling programm by yourself, it's definitly more safe and more clean, especialy when you are a newbie, you should tell me what's going wrong with synaptic.

But anyway, for you make problem, you should install build-essential sudo ```
sudo apt-get install build-essential
```
ubuntu don't deliver compiler and automake by default, yeah i know it's bad :rolleyes:

---

### Post by Nigge on 2006-06-19
I can't connect to the Ubuntu in synaptic, so that's the problem :(

I had tried to write the IP, but it didn't work :(

---

### Post by FredB on 2006-06-19
[QUOTE=givré]Synaptic should work, i think you should try to get it working instead of compiling programm by yourself, it's definitly more safe and more clean, especialy when you are a newbie, you should tell me what's going wrong with synaptic.

But anyway, for you make problem, you should install build-essential sudo ```
sudo apt-get install build-essential
```
ubuntu don't deliver compiler and automake by default, yeah i know it's bad :rolleyes:[/QUOTE]

Not bad, just a matter of space. And not every user of Ubuntu needs gcc and co ;)

---

### Post by givré on 2006-06-19
[QUOTE=Nigge]I can't connect to the Ubuntu in synaptic, so that's the problem :(
I had tried to write the IP, but it didn't work :([/QUOTE]
I don't really understand you, what is the error you have in synaptic? Is it a problem of connectionto the net?

---

### Post by dweez on 2006-06-19
I use Synaptic fine with Drake.  Below is my /etc/apt/sources.list if it helps any.

> ## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

#created by arnierepoadded


---

