---
title: "Introduction, I'm a newbie to Ubuntu"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by Escanor Tanthul on 2007-03-04
Greetings,

I recently reworked my laptop so I've got XP Pro on one partition and I've got Ubuntu 6.06 LTS installed aswell. I am in an IT school and we've used Linux in a few classes but it's all school related lab stuff etc, can't say I really have learned much. I figured I'd install linux to use and play with on my own.

Got a few things to figure out:

1. Is it possible to get limewire installed? I see that they have a linux .rpm file but I don't know how to unpack it / install it.

2. My friends at school use Amarok Media player, I searched synaptic package manager for it and it says its for the KDE Desktop, I imagine I'd have to install KDE to get it to work?

3. Every few minutes my video flashes/flickers for an instant, not a problem but kinda curious if it's a driver issue? I'm on a Gateway laptop with an nVidia 6800 Go video card. Could someone direct me to newer drivers?

Those are just a couple of questions, I'm still quite new to Linux when it's outside the classroom.

Thanks in advance!

Escanor

---

### Post by bikeboy on 2007-03-04
1. If there's only an rpm available, you can install a program called "alien" through Synaptic. Alien can then make a .deb for Ubuntu to install from. It may not always work though,

Some instructions for using alien are at this page, which tells you everything you need to know about software installation on Linux.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

2. That's the beauty of Ubuntu and Synaptic (or apt-get), Amarok does indeed need some kde components, just a few libs (like .dll files) in fact, but you don't need to worry about any of that. Just open up Synaptic, search for Amarok and select for installation, then apply and Synaptic will install all of the required kde parts automatically.

3. Not sure what is causing your issue, but there are official Nvidia drivers available, they coincide with the Windows ones. These drivers are not open source, so they can't be shipped by deafult by Ubuntu (due to Ubuntu's policy) at this stage.

There are several ways to install the Nvidia one and get it going, depending on how new you want it to be. The simplest way is again through Synaptic, the howto is in the Ubuntu wiki.

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

There is also a script that installs new versions quite easily, but you may be less comfortable with that as it uses the command line. Once you've used Linux for a bit you will find it's easy, but it's completely your chioce.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Hope some of that helps.

---

### Post by Denn1s on 2007-03-04
limewire is just a program created by gnutella, try to search it by that name and ull find wath u r lookin for

---

