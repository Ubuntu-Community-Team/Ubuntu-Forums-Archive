---
title: "VirtualBox in the Repositories?"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-09-07
I'd like to run XP PRO in Ubuntu with VirtualBox.
I have ran this the other way around but am now
switching to Linux permanently so it's time for XP to be in
a virtual machine. 

I can't find VirtualBox in the repositories.
Is it not in there?

---

### Post by Seisen on 2007-09-07
Actually VirtualBox has their own repository  now that you can add.

[http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads")

---

### Post by Orbital75 on 2007-09-07
Sorry to be a pain but since I'm new to linux would you mind showing me the
command line string that would enter this for me.

deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) feisty non-free

---

### Post by Terl on 2007-09-07
Why not just click the link and go to the site?  They have a .deb package right there.  Just click it and select open with debi when the box opens up.

---

### Post by Orbital75 on 2007-09-07
Yeah, I guess I could.... I'm new to linux so There are a lot of things that
I didn't know could be done.  Just want to make sure it installs right.
I've had good luck with synaptic packet manager.

So I downloaded the File.
Now I am guessing that I use the Gdebi package installer to install it?

I'm new so I need to learn.

I'm a windows expert but a Linux newbie......

---

### Post by LaRoza on 2007-09-07
> **Orbital75 said:**
> 
I didn't know could be done.  Just want to make sure it installs right.
I've had good luck with synaptic packet manager.

.deb files are like the Windows install (.msi) files. Easy to use, just double click!

---

### Post by Terl on 2007-09-07
> **Orbital75 said:**
> Yeah, I guess I could.... I'm new to linux so There are a lot of things that
I didn't know could be done.  Just want to make sure it installs right.
I've had good luck with synaptic packet manager.

It works perfectly.  I should have added that is how I got my copy.  It is great as there is one all set for Ubuntu.  Great program too.  :)

---

### Post by Seisen on 2007-09-07
To add it to you source list open up your source list by doing this

```
gksudo gedit /etc/apt/sources.list
``` and add whichever line you need depending on which distribution you are running.

```
deb http://www.virtualbox.org/debian feisty non-free
deb http://www.virtualbox.org/debian edgy non-free
deb http://www.virtualbox.org/debian dapper non-free
```

it will be one of these three. Then you need to download the GPG key from Virtualbox which they have directions on there for you to follow. Once you have done all that do this

```
sudo apt-get update
```
```
sudo apt-get install virtualbox 
```

---

### Post by swisscow on 2007-09-07
Add the repository rather than just downloading the deb. That way you get the updates

---

### Post by Orbital75 on 2007-09-07
Thanks... All done and works great  :)

---

