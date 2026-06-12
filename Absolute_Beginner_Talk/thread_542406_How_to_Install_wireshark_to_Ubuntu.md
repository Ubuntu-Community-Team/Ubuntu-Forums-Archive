---
title: "How to Install wireshark to Ubuntu"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by aozkaya on 2007-09-03
I recently installed a ubuntu to a PC. And I am new in Ubuntu.

I am trying to install wireshark, using this command:

sudo apt-get install wireshark

but I get this error:

aozkaya@aozkaya-desktop:/$ sudo apt-get install wireshark
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package wireshark

I have heard that somehow I need to search for a location that has wireshark or ethereal and then run the apt-get command. But I have no internet connection for this PC. Is there any posiiblility to install wireshark without internet connection. Or if I need that internet connection; then how should I search for a location? (by using a command, or using a program?)
This is really urgent.
I really appreciate your helpings..
Thanks,

---

### Post by sumguy231 on 2007-09-03
apt-get won't help you much here, as its job is pretty much to download packages from the Internet and install them. You can always just find the wireshark packages (and anything it depends on) on packages.ubuntu.com, put the .deb files on the Ubuntu installation, and install them.

---

### Post by nowshining on 2007-09-03
yes those apt-gets right there you just did along with system package manager will need to go out to the internet to packages.ubuntu.com repositories to download the program.. so yes an internet connection is required but why no internet - wireshark is a program to monitor internet packets in/out to the internet so without an internet connection the program is pretty much useless..

---

### Post by aozkaya on 2007-09-03
Thank you so much for your quick reply,

I am going to work in a close network, which has 20 PCs that will communicate each other.Therefore I need wireshark for experiments. I have checked that link, there are 24 depends plus wireshark. Do I need to insall all those files to ubuntu? It looks that having a connection will make it much more easy. 

[http://packages.ubuntu.com/feisty/net/wireshark](http://packages.ubuntu.com/feisty/net/wireshark)

Thanks a lot,

aozkaya

---

### Post by nowshining on 2007-09-03
lolz yes having an active internet connection makes the whole process much easier.. :)

---

### Post by splintercellguy on 2007-09-03
Wireshark should be in repos, do you have universe repos enabled?

---

### Post by aozkaya on 2007-09-03
I have not changed anything. If it is not enabled as default, then it might be disable? Could you please tell me, where can I check it from?

Thank you,
aozkaya

---

### Post by splintercellguy on 2007-09-03
System -> Administration -> Synaptic, then Settings -> Software Sources (I think) then check all the repos.

---

### Post by LowSky on 2007-09-03
comes up in add/remove for me

---

### Post by sumguy231 on 2007-09-04
You don't have to install all of those packages, most of them will already be installed since they're just part of the Ubuntu base system. I suggest just getting the wireshark and wireshark-common packages and seeing what you need when you try to install it.

> Wireshark should be in repos, do you have universe repos enabled?
It wouldn't matter without an Internet connection, would it?

---

### Post by aozkaya on 2007-09-04
Thank you so much Sumguy231. Finally I have installed the wireshark. when I install the wireshark-common file then it asked me the missing files: libadnst and libpcre3(>=4.5)
I installed this two files and wireshark-common and wireshark, and right now wireshark is successfully installed.
Thank you for all of you..

---

### Post by acluistic on 2007-09-10
sudo aptitude update
sudo aptitude install ethereal

(This installs wireshark somehow :))

---

