---
title: "synaptic error"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by dhanes on 2006-09-14
I try to install some packages with Synaptic and I get an error like could not download all repository indexes and this link or what:

[http://mirror3.ubuntulinux.nl/dists/dapper-seveas/freenx/binary-i386/Packages.gz:302](http://mirror3.ubuntulinux.nl/dists/dapper-seveas/freenx/binary-i386/Packages.gz:302) Found

I've got an internet connection working and I don't know how to solve this.

---

### Post by oedipuss on 2006-09-14
Have you tried using a different mirror?

---

### Post by dhanes on 2006-09-14
No, something like what? I'm an absolute beginner. Where should I write other mirror?

---

### Post by Najand on 2006-09-14
Click on reload first. then try again.
If it could not solve your problem, try
apt-get:
```

sudo apt-get update

```
and see what error messages you will receive?

---

### Post by dhanes on 2006-09-14
failed to fetch on that link is the message! Now what?

---

### Post by Najand on 2006-09-14
Maybe the mirror is not working now... It sometimes happens...

---

### Post by oedipuss on 2006-09-14
That link 's a mirror for the freeNX repository, right? 
Try editing the file 'sources.list' :

sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
(this is just to keep the original file intact in case something bad happens)
sudo gedit /etc/apt/sources.list

and replace the address of the lines that match the address from your error, with 

deb [http://free.linux.hp.com/~brett/seveas/freenx](http://free.linux.hp.com/~brett/seveas/freenx) dapper-seveas freenx
deb-src [http://free.linux.hp.com/~brett/seveas/freenx](http://free.linux.hp.com/~brett/seveas/freenx) dapper-seveas freenx

respectively.
Or rather, instead of deleting these lines, comment them, by adding a # before 'deb' so that you can easily revert back to them.

---

