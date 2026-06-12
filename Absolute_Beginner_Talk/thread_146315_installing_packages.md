---
title: "installing packages??"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by zinzin on 2006-03-18
where cn i find packages for ubuntu 5.10?
i also need to know hw to install them.
i hv installed ubuntu5.10...i cant run synaptic package manager...can anyone tell me y?...
also i hv got a few rpms. anyway i can use them in ubuntu?

---

### Post by tkiesel on 2006-03-18
Is Synaptic not running whatsoever, or are you being asked for a password that you don't know?

The password that Synaptic asks for is your user password.. the password you created when you installed Ubuntu and that you use to log on.

---

### Post by KansasJoe on 2006-03-18
Depends if your packages are in synaptic or not...if so then sudo apt-get install packagename 

If not and it's rpm then you'll need to first get alien

sudo apt-get install alien

then convert it over

sudo alien -d packagename.rpm

if you have to compile then unzip and then

./configure
make
make install

or some just need to have setup run...read directions for whatever you are trying to get or let someone here know the package and they can help you out

---

### Post by zinzin on 2006-03-18
its not abt the password...wen i click on synaptic package manager,it asks for a password and then nothin appears...
about alien...... do i hav to download package frm net?
 where do i get packages for ubuntu.... in the net?

---

### Post by Jimmey on 2006-03-18
Yes - from the net. The most advisable way of getting software applications is to use Synaptic. To try and see the errors that Synaptic is returning before it quits, I'd suggest you run it from the terminal, with the following command:
> sudo synaptic
That way, you can monitor the programs progress ( or lack of ), in the console window ( once you know what errors Synaptic's giving, you can post them in this forum, and we'll help you sort them out ).

You may want to try editing the repositories:
> cd /etc/apt/
sudo cp sources.list sources.bak
sudo gedit sources.list

And then delete the '#' before the following line of text:
> deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe main restricted
And then save.

Once you've done this, you can try the following:

> sudo apt-get install <package-name> 
so in your case:
> sudo apt-get install alien

---

