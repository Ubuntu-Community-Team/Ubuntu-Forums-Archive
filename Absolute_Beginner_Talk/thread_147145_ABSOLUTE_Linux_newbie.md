---
title: "ABSOLUTE Linux newbie"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by phenix on 2006-03-19
I have just recently installed the latest version of Ubuntu on my old powerbook g3. Well, the thing is that I dont even know how to install apps on this thing. I've downloaded source files to try and install but no luck at all. Any help provided would be greatly appreciated. This is my first time using linux (obviously) and would really like to give it a try. .Is there a distro that would work better on powerpcs (yellow dog maybe)..
Thank you much for the help :confused:

---

### Post by Zelut on 2006-03-19
Of all the distributions I've tried I really think Ubuntu is the most user-friendly.  Lets give it a little more time before moving on ;)

To install programs:
You should have, under "Applications" a menu called Add Applications.  If you open this it should give you a very long list of available applications to install.  You can simply check the box and it'll download & install for you.

Another method is using Synaptic.  You can find that in System > Admin > Synaptic.  In this program you can search for application titles & it can also automagically install them for you.

If you'd share which programs you're looking to install I'm sure we can tell you just how to get it done.. and it'll be much simpler than you expected :)

---

### Post by phenix on 2006-03-19
[QUOTE=kuyaedz]Of all the distributions I've tried I really think Ubuntu is the most user-friendly.  Lets give it a little more time before moving on ;)

To install programs:
You should have, under "Applications" a menu called Add Applications.  If you open this it should give you a very long list of available applications to install.  You can simply check the box and it'll download & install for you.

Another method is using Synaptic.  You can find that in System > Admin > Synaptic.  In this program you can search for application titles & it can also automagically install them for you.

If you'd share which programs you're looking to install I'm sure we can tell you just how to get it done.. and it'll be much simpler than you expected :)[/QUOTE]
THANK YOU so much for the fast reply.....
I have already successfully installed some apps using the methods you pointed out on your response. What I'm really having trouble with, are the source files I download from online. There are instructions on how to download source files, but so far I havent been able to get them to install, especially the ones that have a lot of dependencies. Right now know I was trying to install kompose but with no luck.. These are the steps that I took: 
1- downloaded source file to desktop
2- on the terminal I typed in "tar jzvf kompose-0.5.4.tbz on got a message saying 'try tar --help' whatever that means, and thats where I stopped..

I might be jumping steps or something, but right now I have no idea of what I'm doing or not doing...

Once again thank you much...

---

### Post by aysiu on 2006-03-19
Kompose is in the repositories.

Get extra ones:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Then install Kompose:
```
sudo aptitude update
sudo aptitude install kompose
```

---

### Post by arctic on 2006-03-19
Don't forget to install the build-essential metapackage, otherwise you will not be able to build anything on Ubuntu.

PS: Ubuntu, Fedora and Mandriva are the best choices for Macs (unless you are keen on building from scratch with e.g. Gentoo or Debian)

---

### Post by OffHand on 2006-03-19
This guide helped me a lot to get started: [http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by phenix on 2006-03-19
hey aysiu, 
tried installing the repositories typing in the given commands for Ubuntu (Gnome)
but got the following messege: 'cp: missing destination file'

is there anything else I had to add or have installed before typing in those commands? Thank you much!

---

### Post by phenix on 2006-03-19
hello artic,
is that something that is supposed to be included while I installed Ubuntu, or do I have to look for it, and install it myself? 
thank you!

---

### Post by bionnaki on 2006-03-19
read this: [http://www.psychocats.net/ubuntu/installingsoftware.php](http://www.psychocats.net/ubuntu/installingsoftware.php)

---

