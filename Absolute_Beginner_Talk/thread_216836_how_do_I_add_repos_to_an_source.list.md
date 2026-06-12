---
title: "how do I add repos to an source.list?"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by kris2pe on 2006-07-16
I wanted to install Xgl in my ubuntu. But I'm kinda stuck @ this part of the instruction.
1. Add new repos to your /etc/apt/sources.list.
Anyone here can help me?
anyways is there a way to customize what effect you want & don't want? I wanna still make my system light you know what I mean!!!

---

### Post by Kobalt on 2006-07-16
To add a repos to your sources.list, type in a terminal : sudo gedit /etc/apt/sources.list . But I suggest you make a backup of this file before your touch anything in it. 
For XGL+Compiz, of course you can customize the effects. You'll be able to do so easily with a tool named Gset-compiz. I think you can install it through Synaptic once you've added the Compiz repos. 

Cheers !

---

### Post by philippe_carlo on 2006-07-16
If you know the name of the repository, just add it like this:

deb http://<YOUR MIRROR HERE>/ubuntu dapper <REPOS NAME>

And then type sudo apt-get update. This will only affect your system if you actually install packages from that repository.

---

### Post by Jagot on 2006-07-16
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by adam.tropics on 2006-07-16
> **Kobalt said:**
> To add a repos to your sources.list, type in a terminal : sudo gedit /etc/apt/sources.list . But I suggest you make a backup of this file before your touch anything in it. 
For XGL+Compiz, of course you can customize the effects. You'll be able to do so easily with a tool named Gset-compiz. I think you can install it through Synaptic once you've added the Compiz repos. 

Cheers !

Just a word on gset-compiz. It is a handy tool, but please check around [http://www.compiz.net]("http://www.compiz.net") to be absolutely sure you have the latest version, else it will often crash out Compiz. This doen't matter really as you can just restart Compiz, and configure it using gconf-editor, but it is an irritation. For a little while, and I think perhaps currently, since theming support was added, the most recent version was posted in the forum rather than hosted on the repo.

---

### Post by kris2pe on 2006-07-16
so how do I add gpg key? 
Download and import the gpg key for quinnstorms repository

Code:

wget [http://www.beerorkid.com/compiz/quinn.key.asc](http://www.beerorkid.com/compiz/quinn.key.asc) -O - | sudo apt-key add -

So how do I this step?

---

### Post by adam.tropics on 2006-07-16
paste the entire line into terminal, and press enter

---

### Post by kris2pe on 2006-07-16
when I enter this code I get an error

sudo apt-get update

error:
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg)  Could not connect to packages.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by adam.tropics on 2006-07-16
Close Synaptic, or the add/remove programs, one of them seems to be running

---

### Post by kris2pe on 2006-07-16
I restarted my system & still the same thing happend.
Should I fix this or should I move on?

---

### Post by adam.tropics on 2006-07-16
```
sudo gedit /etc/apt/sources.list
```

and comment out (#) the [http://packages.freecontrib.org/](http://packages.freecontrib.org/) repo for now and try again.

---

### Post by kris2pe on 2006-07-16
> **adam.tropics said:**
> ```
sudo gedit /etc/apt/sources.list
```

and comment out (#) the [http://packages.freecontrib.org/](http://packages.freecontrib.org/) repo for now and try again.

I don't get it!!! DO I have to remove # symbol or do I have to add 
[http://packages.freecontrib.org/repo](http://packages.freecontrib.org/repo) ?
First of all I tried searching 4 this url & its nor posted on the source.list file!!!

---

### Post by adam.tropics on 2006-07-16
a line with # at the front is commented out and does not get read, so put a #  in front of the offending repo line

---

### Post by kris2pe on 2006-07-16
the only "http://packages.freecontrib.org/" in source.list is
this code:
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
I don't see any "http://packages.freecontrib.org/repo".
SO my question is do I have to add it?

---

### Post by adam.tropics on 2006-07-16
my fault for abreviating, sorry. Put # in front of 

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free

and then repeat the sudo apt-get update

---

### Post by kris2pe on 2006-07-16
2. Install:

    * Open Synaptic and search XGL
    * select xserver-xgl
    * search compiz
    * select compiz, compiz-gnome, gset-compiz
    * optionally select gcompizthemer, gcompizthemer-themes
    * apply and exit

I moved in installing compiz-gnome & I get this error

compiz-gnome:

  Depends: libpango1.0-0 (>=1.12.3) but 1.12.2-0ubuntu3 is to be installed

I already installed libpango1.0-0 in the repo!!!

---

### Post by adam.tropics on 2006-07-16
um, check if the followinf repo is in sources.list

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse


If it's not, then add it (or delete the # fromthe front of it) and go again

---

### Post by kris2pe on 2006-07-16
> **adam.tropics said:**
> um, check if the followinf repo is in sources.list

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
I saw it! 
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
what do I w/ it?

---

### Post by adam.tropics on 2006-07-16
no you didn't, that's not it (look at the bit that says 'dapper main' as opposed to 'dapper-updates main'. So if you can't find it, just paste it at the end of the list and go....again!

---

### Post by kris2pe on 2006-07-16
Still the same!!!
I actually posted the code it to source.list
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
in change the au to ph. got the same error!!! 

[COLOR="DarkOrange"]Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz-gnome: Depends: libpango1.0-0 (>= 1.12.3) but 1.12.2-0ubuntu3 is to be installed
[/COLOR]
Sorry I'm difficult to teach!

---

