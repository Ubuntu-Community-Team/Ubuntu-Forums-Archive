---
title: "D-link Airplus DWL-G510 Wireless PCI problem"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by bzzzzz on 2008-04-20
I've just installed Xubuntu using Wubi 8.04 and there appears to be this not uncommon problem of the wireless network card not having the correct drivers.

I've hunted through many of the forums and although there are solutions on offer most of them seem to be assuming that the computer does have an internet connection.

As I don't have the wireless card working I don't have internet and so I'm trying to download the drivers using my laptop and then put them onto a flash drive and then move them over to the desktop that way.

I've moved both ndiswrapper 1.52 and a driver from driverok.  Incidentally I'm not sure if I have the correct driver - I'm not sure how to find out what revision of the card I have.  

My problem at this stage is that I don't know how to install these packages and I'm not sure where I should put them - at the moment they are just sitting on the desktop after transferring from my flash drive.

---

### Post by Hieronymus on 2008-04-20
Ok, an option is to use Ndiswrapper. You already found thaty out. First you have to make sure you have the right windows drivers for you Wlan card.

Then install ndiswrapper

```

sudo apt-get install ndiswrapper-common ndiswrappr-utils-1.9

```

Now install the driver

```

sudo ndiswrapper -i /driverlocation/drivername

```

Now load the driver

```

sudo modprobe ndiswrapper

```

Check if the driver is loaded correctly

```

lsmod | grep ndiswrapper

```

the output should show ndiswrapper

and if you now have wlan

```

iwconfig

```

This should show that one of your cards has a wlan capability

To mak it all work at boot time just put ndiswrapper at the bottom of the file /etc/modules

Jeroen

---

### Post by bzzzzz on 2008-04-20
sudo apt-get install ndiswrapper-common ndiswrappr-utils-1.9

I can't use this command as I'm not connected to the internet

---

### Post by Hieronymus on 2008-04-20
Yes you can, these files are included on the ubuntu image, so just make sure that de cd is still in the repositories (/etc/apt/sources.list)

It should work,

Jeroen

---

### Post by bzzzzz on 2008-04-21
I'm not using a cd either.  I've installed it using wubi

---

### Post by Helios38 on 2008-04-21
pop in the CD when ur running it using wubi

---

### Post by bzzzzz on 2008-04-22
I don't have a cd.

I have managed to install drivers.

I downloaded and placed onto a usb stick ndiswrapper-common and ndiswrapper-utils-1.9 from here
[http://packages.ubuntu.com/hardy/misc/](http://packages.ubuntu.com/hardy/misc/)
I then transferred them to hardy which surprisingly managed to mount my usb automatically.  Double clicking on ndiswrapper-common first unpackages and installs the program for you.  Then I did the same for ndiswrapper-utils-1.9.

I then downloaded the following program which allows you to install drivers using a graphic interface from here

[http://packages.ubuntu.com/hardy/ndisgtk](http://packages.ubuntu.com/hardy/ndisgtk)

I then collected my driver from driverok here
[http://www.driverok.com/en/c/net/d-link/](http://www.driverok.com/en/c/net/d-link/)

there were three revisions for my card, I just guessed and the first time it said my card wasn't recognised, but the second time it did.

I managed to find my wireless connection, but my problems are far from solved.  Initially when I tried to connect, the computer would light the first green light, but then just at the point of connection it would freeze.  I then looked at the properties of  my wireless internet connection and I noticed I had roaming enabled.  I disabled this and now when I try it to connect it doesn't hang.  However when I open firefox it doesn't open.  

So I think I'm connected to the network, but I can't use the internet yet.

I'm going to try and install skype and see if that works.

---

