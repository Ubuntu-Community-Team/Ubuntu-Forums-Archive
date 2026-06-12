---
title: "Help with ndiswrapper"
date: 2006-04-07
forum: Absolute Beginner Talk
---

### Post by Adrnshw6 on 2006-04-07
Hi everyone, now that I have ubuntu installed, I am trying to get my wireless card (WMP54GS) to work.  Apparently, I need a program called ndiswrapper to install the Windows drivers onto ubunto.  So, I went to system/administartion and went into Sinaptic Package manager.  I searched for ndiswrapper, and installed it.  To my knowledge, a new option was to be available in system/admin called "Windows wireless drivers"

I have no new option.  Is there something I missed?  Something else I need to install?  

Thanks for the help!

---

### Post by trent dillman on 2006-04-07
Open a terminal:

```

sudo modprobe ndiswrapper

```

Get a copy of the Windows drivers for your card (should be a .sys and a .inf).

Here's a nice GUI for installing them:

```

sudo apt-get install ndisgtk
sudo ndisgtk
```

Then open the .inf file. You should be able to configure your card with the Network Manager from there...

---

### Post by Adrnshw6 on 2006-04-07
I typed in "sudo modprobe ndiswrapper" and it said "FATAL: Error inserting ndiswrapper

Also, the driver is a .exe, there is no .sys or .inf

---

### Post by trent dillman on 2006-04-07
OK, some work for you then. :-)

First, let's get ndiswrapper working:

```
sudo -s
apt-get install ndiswrapper-source build-essential
cd /opt
tar jvxf /usr/src/ndiswrapper-source.tar.bz2
cd ndiswrapper*
make install
modprobe ndiswrapper

```

As for the .exe, you may try installing wine...

What wireless card do you have?

---

### Post by Adrnshw6 on 2006-04-07
[QUOTE=trent dillman]OK, some work for you then. :-)

First, let's get ndiswrapper working:

```
sudo -s
apt-get install ndiswrapper-source build-essential
cd /opt
tar jvxf /usr/src/ndiswrapper-source.tar.bz2
cd ndiswrapper*
make install
modprobe ndiswrapper

```

As for the .exe, you may try installing wine...

What wireless card do you have?[/QUOTE]


Tried what you said and at ```
apt-get install ndiswrapper-source build-essential
```  it said 
"Reading package lists...Done
Building dependency tree...Donr
Package ndiswrapper-source is not available, but is referred to by another package. 
This may mean that the package is midding, has been obsoleted, or is only available from another source"

What does that mean?  BTW I am trying to install a Linksys WMP54GS card.

---

### Post by trent dillman on 2006-04-07
Sounds to me like you need some extra repos. I'd try wiki.ubuntu.com/AddingRepositoriesHowto for that. In the meantime, you can visit ndiswrapper's site and get the source.

---

### Post by Wallakoala on 2006-04-07
[QUOTE=trent dillman]Sounds to me like you need some extra repos. I'd try wiki.ubuntu.com/AddingRepositoriesHowto for that. In the meantime, you can visit ndiswrapper's site and get the source.[/QUOTE]

Go to synaptic and search for ndis. There should be something like "ndiswrapper-utils" Install that. Wherever you got that .exe from, there should also be a .inf and .sys. Did you get it from the cd? If you did, copy the .inf and .sys to your home directory, and then in the terminal do ```
ndiswrapper -i INSERTNAMEOF.infHERE
```
And change INSERTNAMEOF.infHERE with the name of the .inf file that you got from the cd. Then, do ```
ndiswrapper -l
```
If your output says something like "NAMEOFDRIVER : Driver loaded, hardware present" where NAMEOFDRIVER is the name of the driver, then you are on the right track. Do ```
modprobe ndiswrapper
```
and your internet SHOULD work. I might be leaving something out, it has been a while.

---

### Post by Wallakoala on 2006-04-07
alright, turns out you aren't supposed to use the drivers from the cd. Go here: [https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?highlight=%28ndis%29](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?highlight=%28ndis%29)

Follow the directions, read carefully.

---

### Post by Adrnshw6 on 2006-04-07
The thing is, the firmware off linksys.com is only a .exe, no other files at all.

---

### Post by trent dillman on 2006-04-08
install wine, and then use that to 'install' the files to a fake c drive

then you can install them for real

---

### Post by javaJake on 2006-04-12
I have a WMP54GS card as well. You do not need to install wine, or even touch the EXE files. However, be warned that Ubuntu 6 and up will not work with this card, as reported in this bug ([https://launchpad.net/distros/ubuntu/+source/base-config/+bug/34326](https://launchpad.net/distros/ubuntu/+source/base-config/+bug/34326))

To install your card in Ubuntu 5.10, just run...
apt-get install ndiswrapper-utils

This requires that you still have your install CD.
Once installed, insert your Linksys install CD, mount it, and run...

sudo ndiswrapper -i /cdrom/Drivers/BCMWL5.inf
sudo modprobe ndiswrapper

This should work. Instantly you should be able to edit your wireless network settings and connect. Again, this will not work in Ubuntu 6! While ndiswrapper will accept the driver, Ubuntu will not recognize the wireless card correctly!

Reply if you need any more help.

---

### Post by MrSt0ne on 2006-04-14
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-10-386/misc/ndiswrapper.ko): Invalid argument

This is the message I get when ii try to do sudo modprobe ndiswrapper.
I need help the cord comming from my computer from my router is killing me. Please help

---

