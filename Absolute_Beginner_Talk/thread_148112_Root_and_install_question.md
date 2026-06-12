---
title: "Root and install question"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by geek_overlord on 2006-03-21
This is the second Linux distro I have tried (couldn't network with Suse) and I am very impressed with Ubuntu. I was able to dualboot on my sata drive with no issues. Everything I needed to get started was installed with minimal hassle. I deciede to get another hard drive (ide) for Ubuntu but I need to know if there will be an issue with the large volume (200g)? Windows can't see the volume unless I install sp1 or limit the size to <137g. I also need help with root. I set up one account with a usr name and password but I wasn't asked to create a root account. Can someone point me in the right direction for setting up a usr and root acct? Thanks in advance for the help.
This distro rocks.:-D

---

### Post by neoroses on 2006-03-21
ok - well firstly you dont actuly need to setup a root acount on ubuntu if u wanna run a root operation just type:

```
sudo
```

it will then ask you for a password - just use your user one

but if you want to set up a seperate root account with its own password use:

```
sudo passwd root 
```

and if you want to run a program that you cannot do from a terminal as root do 

application -=-> system tools --> run as differnt user

hope i could be help...im not expert tho

---

### Post by AtinLango on 2006-03-21
The password of that account you created during install is the one which opens you to root privileges. Whenever you want to work as root you will have to supply that password. The password will be asked automatically in certain instances e.g. when you go to System/Administration/Networking.

When at the terminal and you want to be like root, you have many ways. One of them is to type 

```
sudo bash
```

then supply that password and you will be able tp execute root commands.

---

### Post by pbaehr on 2006-03-21
Check out this page for more information on root and sudo.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

If you decide you do want to enable root it tells you how to do it toward the end.

As far as the large drive, I don't expect you'd have any trouble. My ubuntu install has a 200 gb hard drive, but it was there since install. Though, recently I added a 200 gig hard drive to a debian system at work without it flinching. So in my experience it won't be a problem.

---

### Post by halfvolle melk on 2006-03-21
Some usefull links:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[https://wiki.ubuntu.com/AddUsersHowto](https://wiki.ubuntu.com/AddUsersHowto)

---

### Post by geek_overlord on 2006-03-21
Thanks very much for the help with this. I feel much better about the usr acct I created now. I'll read through the links provided. There is so much to learn but I haven't been this excited about an os in a long time. \\:D/

---

