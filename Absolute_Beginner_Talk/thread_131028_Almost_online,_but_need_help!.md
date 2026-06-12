---
title: "Almost online, but need help!"
date: 2006-02-15
forum: Absolute Beginner Talk
---

### Post by ladyeldawen on 2006-02-15
Hi there, currently using my windows machine to get online here. I am almost online (dialup) with Ubuntu I think, but I've hit some setbacks. I found the Linux versions of the drivers for my modem (Intel 536EP PCI), but they only come in .tgz format. I was instructed to do the following:

 tar -xvzf [filename].tgz

 Then "cd" (any idea what that means, anyone?) into the directory created and type:
make clean
make 536EP
make install

or

./configure
make
sudo make install

 My problem? Every single time it says "make command not found"

 Please do what you can to help. I've used windows my whole life and am eager to switch. thank you.

---

### Post by gord on 2006-02-15
you need the build essential package to compile the driver
```

sudo apt-get install build-essential

```

also, cd meens Change Directory

---

### Post by ladyeldawen on 2006-02-15
Thank you for your speedy reply, gord.

 I'm afraid I've tried apt-get many times on Ubuntu, but it seems to fail as I have no working internet connection, which I'm working on. Is it possible to find this package online and transfer it to the linux machine with a memory stick or the like? Will this package solve the "recognizing make command" problem? Thank you for your patience with my low skills lol.

---

### Post by dabear on 2006-02-15
install checkinstall too, and then run this to install:
```

./configure
sudo checkinstall

```
This way, you'll get a .deb package that you can remove using synaptic or the command line

---

### Post by arctic on 2006-02-15
[QUOTE=gord]you need the build essential package to compile the driver
```

sudo apt-get install build-essential

```

also, cd meens Change Directory[/QUOTE]
Yeah, he needs the build files, but how shall he install them with apt-get? Can you tell me? :rolleyes: :rolleyes: :rolleyes: 

you will need to download the files from an ubuntu mirror one by one and install them by hand first before you can compile the driver. You ran into a nice problem. I don't know if you want to hear this, but my recommendation is to install a linux-system that ships with the build-essentials, like e.g. fedora or suse or debian or ...

This is sadly one scenario where you are nearly lost with ubuntus one-CD only approach imho.

---

### Post by ladyeldawen on 2006-02-15
Thank you as well, dabear!

 I'm assuming that I can find said packages above online through windows, and simply transfer them to my other machine via memory stick?

 checkinstall will create a .deb package that I can install with k-package, correct? Thank you.

---

### Post by ladyeldawen on 2006-02-15
Yes, that's the problem I noticed. However, I've gotten past a few of them by finding the packages online with windows, saving them to a USB memorystick, and then booting into Linux, but I'm not sure if that'll work in all cases.

---

### Post by gord on 2006-02-15
make sure your ubuntu breezy install cd is in your cdrom and try apt-get again, build essential is on the cd

if its not recognised type
```

apt-cdrom add

```
and try again

---

### Post by Bartender on 2006-02-15
Can you get your computer to some place with a network?  Work?  School? Library?  A friend's house?  I'm in the exact same predicament you are - dial-up and no connection yet.  I went into the networking section from the main menus on the top of the desktop screen and "enabled" the network interface card (if you have a network card or onboard networking this will be eth0 in almost all cases).  Then I lugged the machine into work, borrowed a cable off one of the networked machines, & plugged it into the Ubuntu PC BEFORE turning it on.
Was online without a hitch.  I didn't change any networking settings (DNS, WINS, DHCP, etc.).  Just took a chance.  If it worked for you, just a few hours of borrowed internet connection would be enuf to do the things that have been suggested above, plus download & install firestarter (firewall), clamav (anti-virus), maybe you'd want to download/install Automatix because it would take a week on dial-up!

---

### Post by ladyeldawen on 2006-02-15
Hey, glad to hear it's working out a bit better for you! Access to a cable line/DSL etc IS possible, but the cover to the tower is almost falling apart, and very heavy to just lug around. How goes your dialup, have you gotten it to work yet? I found the exact linux drivers for my winmodem, but can't seem to install them. Go figure.

---

### Post by towsonu2003 on 2006-02-16
just came accross this one (I'm not stalking :PpPp) and wanted to give this link to anyone doing a search for this modem on the forum: [https://wiki.ubuntu.com/DialupModemHowto#head-068a426acfdc8518889ea095253c50b665bce5d4](https://wiki.ubuntu.com/DialupModemHowto#head-068a426acfdc8518889ea095253c50b665bce5d4)

:twisted: 

PS. at one point, I tought there was an ongoing sale for this modem or something. don't wanna miss a sale :PpPp 

Notice: no offense intended

---

