---
title: "Ubuntu: How do you set permissions?"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by gsk320 on 2007-03-03
how do yo set permissions. I am trying to put java on ubuntu 6.06 and it wont let me copy to the "/opt/" directory saying "you do not have permissions to write this folder" I am the one who set up Ubuntu on my computer, and the only account on Ubuntu is mine. So please help me

---

### Post by taurus on 2007-03-03
Applications -> Accessories -> Terminal
```
gksudo nautilus
```
or
```
sudo cp **filename** /opt
```

---

### Post by steve101101 on 2007-03-03
also to change permissions of a folder type this

sudo chown USERNAME /FILEPATH

or 

sudo chown -R USERNAME /FILEPATH

if you want to change permissions of all files and folders within the FILEPATH.

---

### Post by aysiu on 2007-03-03
I don't think changing ownership of system folders is a good practice to encourage.

taurus is on the right track. More details here:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by maniacmusician on 2007-03-06
> **aysiu said:**
> I don't think changing ownership of system folders is a good practice to encourage.

taurus is on the right track. More details here:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)
I encountered a similar situation when I was using Edgy. The thing was, that Automatix was installing Azureus in  /opt (which was fine with me; for Azureus, I like manually installing/installing through Automatix, as it gives me better results than getting it from the repos. Easier on the eyes...the one from the repos is just ugly because of some GTK things that Ubuntu does). Err back on track;

Automatix was installing Azureus in /opt, which is okay because that was pretty much the only thing in there, but I would need admin permissions to be able to write to /opt. Which also meant that I couldn't do updates with Azureus unless I started it as root. So I usually just chown /opt or /opt/[azureus dir]. Doesn't really cause any adverse affects, because the only things I've ever seen in there are VirtualBox and Azureus when I put it there.

---

### Post by Karl S. on 2007-03-07
> I am the one who set up Ubuntu on my computer, and the only account on Ubuntu is mine.

To get to the heart of the matter: there are many tasks you cannot execute unless you execute them as a [superuser (sudo)]("http://www.gratisoft.us/sudo/intro.html"). That's a good thing.

---

