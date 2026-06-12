---
title: "Cinelerra woes"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by linuxnooby on 2007-05-24
I have followed the instructions from various threads, on how to install Cinelerra and, after running the command  

sudo apt-get update

I get the following error message , after the packsages have been read :-

" GPG error: [http://www.debian-multimedia.org](http://www.debian-multimedia.org) sid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: You may want to run apt-get update to correct these problems"

I ignored this and went ahead with

Sudo apt-get install cinelerra

After the install, I clicked on the Cinelrra icon, in Applications and all I got was a fleeting glimpse of a screen outline, the nothing.

The additional entries I made in  /etc/apt/source.list file, are :-

deb-src [http://www.kiberpipa.org/~minmax/cinelerra/builds/sid/](http://www.kiberpipa.org/~minmax/cinelerra/builds/sid/) ./
deb [http://www.debian-multimedia.org/](http://www.debian-multimedia.org/) sid main
deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/athlonxp/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/athlonxp/) ./

Could some kind person explain what I might have missed. I am running Ubuntu 7.04, Amd XP processor and Nvidia GLX graphics.

---

### Post by dbbolton on 2007-05-24
launch it from the terminal by typing 'cinelerra' and post the output

---

### Post by linuxnooby on 2007-05-24
Here is the output:-

Cinelerra 2.1CV (C) 2006 Heroine Virtual Ltd.
Compiled on Tue Apr 24 13:45:37 UTC 2007

Cinelerra is free software, covered by the GNU General Public License,
and you are welcome to change it and/or distribute copies of it under
certain conditions. There is absolutely no warranty for Cinelerra.
Illegal instruction (core dumped)

---

### Post by Matt Nichols on 2007-05-25
I am having a similar problem (exactly the same, actually), and would greatly appreciate a solution. I tried everything suggested here, and nothing worked. Any ideas would be appreciated...

---

### Post by dbbolton on 2007-05-25
you might have to install it from another repo :/

---

### Post by mitch_feaster on 2008-06-25
> **linuxnooby said:**
> I have followed the instructions from various threads, on how to install Cinelerra and, after running the command  

sudo apt-get update

I get the following error message , after the packsages have been read :-

" GPG error: [http://www.debian-multimedia.org](http://www.debian-multimedia.org) sid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: You may want to run apt-get update to correct these problems"

I ignored this and went ahead with

Sudo apt-get install cinelerra



Those who may have this same issue should see [http://cvs.cinelerra.org/getting_cinelerra.php#ubuntu](http://cvs.cinelerra.org/getting_cinelerra.php#ubuntu) for some excellent installation instructions.

---

