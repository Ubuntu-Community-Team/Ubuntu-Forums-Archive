---
title: "Help! Installing programs!"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by LostinLinux on 2006-04-09
Hi, i have searched the forum, but unable to find the answers :(

I have ubuntu installed on my laptp but do not have any internet connection with it. I wish to install the required bluetooth components to enable my PCMCIA card to pair with my phone. 

So, i proceeded to download:

libbtctl-0.6.0.tar.gz
gnome-bluetooth-0.7.0.tar.gz

I assume that is what i need :( Although in the "add new application" tool there are many other bluetooth packages, however i cant get to them becuase of my lack of net access :(

Anyway, i managed to extract the packages and in terminal i get to the:

./configure 

(on alot of the checks here i get "no")

then i go to:

make

but i get the "command not found" return.

What am i doing wrong? I really love ubuntu but without a net connection it seems to be a real hassle,

best regards

---

### Post by teet on 2006-04-09
try typing in the terminal

sudo apt-get install make

That should clear up the "command not found" problem.

-teet

---

### Post by Kimm on 2006-04-09
I sugest

apt-get install build-essentials

that will get some other things the build might like to have...

---

### Post by nalmeth on 2006-04-09
This person does not have internet though.
make is a command that comes in the build-essential package (I believe). If you get the build-essential package you should be able to comile the app.
If you can though, get a .deb instead. To install a .deb file (an ubuntu .deb of course) do this:
sudo dpkg -i package.deb
this won't require the internet if you have the package.
apt-get does require the internet, but uses dpkg for the actual installation of the package.
hope this helps!

---

### Post by teet on 2006-04-09
[QUOTE=nalmeth]This person does not have internet though.
make is a command that comes in the build-essential package (I believe). If you get the build-essential package you should be able to comile the app.
If you can though, get a .deb instead. To install a .deb file (an ubuntu .deb of course) do this:
sudo dpkg -i package.deb
this won't require the internet if you have the package.
apt-get does require the internet, but uses dpkg for the actual installation of the package.
hope this helps![/QUOTE]

Maybe I'm mixed up, but if I remember correctly the build-essential package doesn't actually have to be downloaded.  It just has to be installed.  Don't ask me why it isn't installed by default if it's just sitting there.

But yeah, look for a *.deb file instead.  It will most likely be less hassle.

-teet

---

### Post by nanotube on 2006-04-10
its true that build essential is just a "meta package" that does not install anything for itself - it does however pull down a lot of the dependencies, such as make, gcc, etc - and those DO have to be downloaded. just fyi.

---

### Post by Sutekh on 2006-04-10
No no.  Build-essential and the dependant packages are on the installation CD.

Use this code, and chuck in the CD when required
```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
```

That's the easy part.  The real hassle will be when the ./configure process comes up with packages that are needed, which you will have to fetch and install manually (the dpkg -i way).  Ubuntu without an internet connection *is* a hassle.  For what reason do you not have one?  I don't mean this to be a silly question.

---

