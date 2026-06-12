---
title: "32 bit to 64 bit gutsy and keeping home partition"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by Scotty562 on 2007-11-16
This is what I would like to do. I have a 64 bit processor so  I would like to install 64 bit gutsy overtop of my 32 bit gutsy. I have a feeling this isn't possible which leads to solution 2. 

Could I:
1. copy my /home partition to my xp partiton
2. format my gutsy partion
3. make a / partition and a /home partition (while installing 64 bit gutsy)
4. copy my home partition from my xp machine to my new /home partition?

I want to keep all of my settings and whatnot which I think the home partition keeps most if not all of this. I'll just have to remember to not forget my virtual machine.

---

### Post by uclalinux on 2007-11-17
I don't know if that would work or not, there are a lot of things that might be different, I tried that once and came up with a lot of error's. Here is a way to put your home on its own partition, then you could reinstall and mount that partition, an your home.

How to make your own home partition, [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by mellowd on 2007-11-17
or your could tar your home partition, copy it to a safe location, nuke the drive, install fresh, copy your tar file back over and untar to your home partition again

---

### Post by Inxsible on 2007-11-17
It wouldn't work that way. I moved from 32 bit feisty to 64 bit gutsy. and i did a fresh install.

There is no telling what particular settings will be required for the changed architecture. you are better off with installing it fresh. It took me 40 mins to set up all the apps that i wanted, the way i wanted.

---

### Post by Scotty562 on 2007-11-17
Hmm... thanks for the advice. I think I should juts be happy everything works :). It's too bad you can't keep your home folder when you install a reinstall.

---

### Post by mellowd on 2007-11-17
You could've backed the home dir up and then restored it though

---

### Post by philinux on 2007-11-17
I asked this question in the 64 forum and was told that as I had home on separate partition it should be no problem at all.

---

