---
title: "More stupid newbie questions"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by davebo on 2007-05-09
I am running Ubuntu 7 from a CD at the moment. Guess what ? No wireless. I have the driver from the manufacturer for Linux 2.6. Will this work ? If so, how the heck do I associate the driver with the hardware. lshw knows the card is there.

I've run the makefile on the driver. Now what do I do ?

Sorry to be a dunce.
Davebo.:confused:

---

### Post by Kobalt on 2007-05-09
If it's a basic compilation then you need to run ```
./configure
make
sudo make install
```
Which type of card is it precisely ?

---

### Post by davebo on 2007-05-09
Thanks Kobalt.

I don't understand the commands I need to enter. Do I type them exactly as you've listed ? There doesn't seem to be anything specific to the card there.

It's a Realtek RTL8180L.

Cheers, Davebo.

---

### Post by teddybairs1 on 2007-05-09
What is the file name for your driver? Is it an RPM or a tar.gz?

---

### Post by davebo on 2007-05-09
Thanks TB,

It was a tar.gz. I WinRAR'd it onto a pen drive and then ran the makefile on the Ubuntu PC. It ran it in Terminal and some output flashed past. Then it was gone.

Sorry, I did say I was a dunce.

---

### Post by Kobalt on 2007-05-09
You don't really need these drivers, Feisty has a built-in module that supports your card, but it may be unstable, so it's disabled.
The disabled modules can be found in the /etc/modprobe.d/blacklist file. 
If you want to unblacklist them you need to edit the file : ```
gksu gedit /etc/modprobe.d/blacklist
```
At the end of the file you should find this section concerning your hardware : > # buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187
Make it look like this in order to authorize the modules to load at boot time : > # buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
# blacklist r818x
# blacklist r8187
Reboot and you should be set. **Beware** : as you can read it may cause kernel bugs.

---

### Post by davebo on 2007-05-11
OK,
managed to get the blacklist updated (after running it via sudo).

I even have a network connection to my router. However, firefox can't see t'Internet.

Anything else needs setting up ?

Thanks (again) in advance.
Davebo.

---

### Post by Bachstelze on 2007-05-11
How did you setup your connaction ?

---

### Post by davebo on 2007-05-12
Once I had removed the drivers from the blacklist I just rebooted and it picked up the card. That gave me a wireless link in the network setup (as per the basic connection advice). Once I enabled that, it autdetected the two wifi networks (one of which was mine). Et viola, the network icon (in the top right toolbar) was active.

However, Firefox still can't see t'Internet.:(

Come to think of it, I can't see anything else on the network (like the router). All I can ping is the localhost.

:((

---

### Post by davebo on 2007-05-13
I'm confused. The card is linstalled and the I can see the networks around me, but I can't ping anything but localhost. I've tried setting all manner of DNS entries. I've tried pppconfig too.

If I can't make this work, I'll have to start the long 'walk' back to Windoze and I really don't want that.

:-(

---

### Post by Bachstelze on 2007-05-13
Seeing the networks is not all, you also need to connect to them ;)

---

### Post by davebo on 2007-05-14
Sorry, how do I connect ?

#-o

---

### Post by gigaferz on 2007-05-14
hello, if its wireless

you can get your self either a deb file, or a ubuntu package.

The package you can try is wifi radar.

download it and install it in your ubuntu machine.

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

you only need to right click it and install it,

I am pretty sure by typing a few commands you can scan and connect to networks, but, i dont know them,

---

### Post by davebo on 2007-05-14
Okay, wifi-radar lists my network. The strength bar shows nothing and a <disconnect> button is showing. No <connect> button shows and when I press <edit> nothing happens.

I can't post screenshots because I can't get them off the machine.

Sorry, but I'm still no further forwards and I am losing all hope.

---

### Post by forrestG on 2007-05-16
try this:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78255](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78255)

on your /etc/network/interfaces
search for essid under wlan0
and add a dummy character to your id

for example "essid mywireless" become "essid mywirelessS"

in fact if i try iwconfig before Ubuntu tells me that my essid is "mywireles" and after "mywireless".

But now i have another problem...
removing the 818x from the blacklist GNOME don't want to start... after the login it stops.
but if i connect to Ubuntu by the console all is OK...

Good luck
Damn!

Ciao
Yuri

---

### Post by davebo on 2007-05-22
:p:p:p
Wahey! Adding the extra character worked! I am now connected and typing this from Ubuntu.

Thanks to all for their help. Just when I thought I'd have to abandon Ubuntu.

Cheers, Davebo.

---

