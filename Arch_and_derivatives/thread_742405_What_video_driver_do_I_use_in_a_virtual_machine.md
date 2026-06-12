---
title: "What video driver do I use in a virtual machine?"
date: 2008-04-01
forum: Arch and derivatives
---

### Post by TheOrangePeanut on 2008-04-01
I'm gonna install Arch on a virtual machine and if I can get it set up and working the way I want, I'm going to install it on my main PC.  I was wondering: what graphics driver to I choose since virtualbox emulates the graphics card?  VESA?  Also, how do I install guest additions so I can run the virtual machine at a higher resolution?

---

### Post by pseudo-random on 2008-04-01
You need to download the guest additions .iso and mount it from within virtualbox. Then install it from there.
You're right in saying VB emulates the graphics. The driver is also therefore provided.

---

### Post by TheOrangePeanut on 2008-04-01
Hrm, I didn't even make it that far.  

I followed the beginner's guide like I always do, but I'm not getting a connection in the virtual machine.  ifconfig shows my install having an ip address, and I've configured my hosts file... any idea what could be wrong?  I can't ping google is how I know I'm not getting access to the internet.  I've done this probably 5 times on a real PC and I've always had internet right away... could it be something to do with the virtual machine?

---

### Post by Bakey on 2008-04-29
I had to setup bridged Ethernet on my XP box to get this working, since the NAT interface didn't work under Arch.  Check out section 6.4 of the UserManual.pdf here: [http://virtualbox.org/download/UserManual.pdf](http://virtualbox.org/download/UserManual.pdf)

---

### Post by FredB on 2008-04-29
For arch, in order to setup X, you will have to do this in root :

```
pacman -S hwd libx86 xorg
hwd -u
hwd -xa

```

That's it. Your X will be setup.

---

### Post by gpan on 2008-06-16
> **FredB said:**
> For arch, in order to setup X, you will have to do this in root :

```
pacman -S hwd libx86 xorg
hwd -u
hwd -xa

```

That's it. Your X will be setup.

I did the above, but my virtualbox still doesn't seem to start in graphical mode. I get the following errors:

[[IMG]http://img394.imageshack.us/img394/4129/19962629ty1.th.png[/IMG]](http://img394.imageshack.us/my.php?image=19962629ty1.png)

---

### Post by FredB on 2008-06-16
Choose yes. You'll get a working xorg.conf file.

---

### Post by gpan on 2008-06-16
> **FredB said:**
> Choose yes. You'll get a working xorg.conf file.

First thanks for the reply. I chose yes (it says vesa is ready) but when I type reboot, I don't come into the graphical mode (my kdemod as well as guest additions are already installed). Do I have to edit the xorg.conf in order to get it work? 
:(

---

### Post by Barrucadu on 2008-06-16
To automagically start X you'll need to install a display manager, and edit your /etc/inittab file. The comments in there are fairly self-explanatory.

---

### Post by gpan on 2008-06-16
I have added @kdm at the end of daemons into my /etc/rc.conf but still nothing. :confused:

---

