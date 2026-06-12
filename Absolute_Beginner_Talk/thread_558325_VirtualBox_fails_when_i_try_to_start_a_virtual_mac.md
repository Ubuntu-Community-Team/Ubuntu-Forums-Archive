---
title: "VirtualBox fails when i try to start a virtual machine. i have the error code."
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by ijason on 2007-09-23
hey all. i'm sure this is a quick fix for people who know more about ubuntu than me. i just installed VirtualBox on my 7.04 build, and it's giving an error when i try to run the virtualbox i just created for windows xp. here's the error code that it pops:

> Unknown error creating VM (VERR_HOSTIF_INIT_FAILED).
VBox status code: -3100 (VERR_HOSTIF_INIT_FAILED).

Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

i checked to make sure that my user is a member of the group virtual box set up. and this error is popping on the first "start" of the virtualbox, i haven't had a chance to set up the guest media yet. 

any suggestions?

---

### Post by Dr Small on 2007-09-23
I have never set up a windows os on virtual box, but you could try a Linux distro and see if you get the same error. If not, then we need to look deeper into Windows. If so, then we need to look more throughly through VirtualBox.

Dr Small

---

### Post by ijason on 2007-09-23
**@dr.small **: like i said, i didn't even get to the point of installing the guest OS.

---

### Post by Dr Small on 2007-09-23
So... you mean, VirtualBox isn't even launching ?

---

### Post by ijason on 2007-09-23
**@dr. small** : the *program* VirtualBox installed just fine. and i went through the steps to "set up" a virtual machine on it, but when i try to start that virtual machine to install the windows guest OS and that's when i get the error.

thanks for trying to help so far!

---

### Post by stmiller on 2007-09-23
Ask on [their forum]("http://forums.virtualbox.org/"), perhaps. They have developers who respond. You might have to adjust the ACPI settings for Windows before making a windows VM.

---

### Post by zabec7 on 2008-01-15
I got same problem. I had problem with rights for /dev/net/tun so I added to end of /etc/rc.local:

 chown <user> /dev/net/tun
 chmod 666 /dev/net/tun

Change <user> for your username.

I hope some daemon doesn't change it later on, but for now it works.

---

### Post by boriquajake on 2008-01-15
> **zabec7 said:**
> I got same problem. I had problem with rights for /dev/net/tun so I added to end of /etc/rc.local:

 chown <user> /dev/net/tun
 chmod 666 /dev/net/tun

Change <user> for your username.

I hope some daemon doesn't change it later on, but for now it works.

It looks like you are giving exactly the instructions that I need but I don't quite understand them. Where do I go to access /dev/net/tun and how do I add to the end of /etc/rc.local:?

---

