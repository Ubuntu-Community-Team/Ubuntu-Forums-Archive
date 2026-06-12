---
title: "Ethernet set up"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by OldDog11 on 2007-03-30
I'm trying to setup my onboard ethernet adapter. I have an Asus M2N motherboard.

I tried entering
sudo pppoeconf into the terminal and got this messge.

NO INTERFACE FOUND
Sorry, no working ethernet card could be found. If you do have an interface card which was not autodetected so far, you probably wish to load the driver manually using the modconf utility.
Run modconf now?
Yes No

I select Yes and nothing happens, the same screen just flickers and re-appears.

Does anyone know what I am doing wrong?

---

### Post by openix on 2007-03-30
Try this line in a terminal,

sudo apt-get install modconf

then try,

sudo pppoeconf

this time when asked to run modconf it should launch.

---

### Post by OldDog11 on 2007-03-30
I entered sudo apt-get install modconf

but it replied
couldn't find package modconf

I have looked in the Synaptic Package Manager but it's not there, where is it?

---

### Post by OldDog11 on 2007-03-30
Can anyone help me find modconf please?

---

### Post by zvacet on 2007-03-30
system>administration>network settings>highlight your modem>properties>choose type of connection>chek upper left box>close.In DNS tab insert your nameserver>close.
```
pppoeconf
```

---

### Post by Maestro23 on 2007-03-30
> **OldDog11 said:**
> Can anyone help me find modconf please?

It's there. Do you have extra repositories enabled?  If not:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

or

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by Kamu on 2007-03-30
modconf should be in the universe repository.  Make sure you have that enabled in your sources.list.

Edit /etc/apt/sources.list to make sure that you have lines that look something like:

deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) edgy universe

and that they are uncommented (no # in front).  Note that this is pasted from my sources.list file and that I use swedish mirrors, you may want to pick other ones that are geographically closer to you.  Also, this is for edgy eft.  For dapper drake , you need to have "dapper" instead of "edgy".

---

### Post by compmodder26 on 2007-03-30
OldDog11, you have two open threads about the same issue.  In the other thread, you say you are connected to a router via your ethernet card.  With that setup, you don't need to worry about any modem config tools or pppoe.  This thread should be closed and attention should be paid to the other one.

---

### Post by OldDog11 on 2007-03-30
I tried to load the extra repositories but it seems you need an internet connection.

PROBLEM I am trying to get the LAN adaptor working to get an internet connection on that computer.

It seems every thing I try hits a brick wall!

---

### Post by Maestro23 on 2007-03-30
> **OldDog11 said:**
> I tried to load the extra repositories but it seems you need an internet connection.

PROBLEM I am trying to get the LAN adaptor working to get an internet connection on that computer.

It seems every thing I try hits a brick wall!

You can get it at: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Download it onto a flash drive, blank cd, etc.. and install it on the system that is not connected to the net yet.

---

