---
title: "Network Card installing HELP"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by beezkneez2005 on 2007-03-10
Ok im having an issue installing my driver. it is a DGE-530T (dlink) and ive unpacked it from what i see. and now it is telling me to type cd DriverInstall so i do, then i is in the DriverInstall folder, then it has me type ./install.sh and when i do that i get an error.

./install.sh: 68: Syntax error: "(" unexpected

I dont know what to do know... Im stuck :(

PS: I Am logged in as root.

---

### Post by gradedcheese on 2007-03-10
which Ubuntu?  If it's edgy, then run "bash" to switch to the bash sell before running ./install.sh to make sure it's not a bash syntax in dash thing...

incidentally, what does line 68 of install.sh look like?

---

### Post by beezkneez2005 on 2007-03-10
Its xubuntu. i ordered it from ondisck...

---

### Post by gradedcheese on 2007-03-10
I mean which release?  6.06? 6.10?

---

### Post by beezkneez2005 on 2007-03-10
its version 6.10

What command do i need to type in or can you give me step by step instructions on what i do, Thanks in advance.


Edit: I figured out that when im in the DriverInstall folder and i go to terminal and log into root, and type 
sudo bash install.sh

It runs threw the install. Everything checks ok accept for 1 thing fails.  the Check kernel Header files (not found) [failed]

Were do i get this file?

It says "Please install the linux header files development package or crate a symbolic link from the /usr/src/KERNEL_VERSION /usr/src/linux"

---

### Post by gradedcheese on 2007-03-10
run:

```

sudo apt-get install linux-headers-`uname -r`

```

to get the headers.  You need the compiler too:

```

sudo apt-get install build-essential

```

oh, and if you haven't used apt-get on this PC yet, first run:

```

sudo apt-get update

```

---

### Post by beezkneez2005 on 2007-03-10
When i type sudo apt-get install linux-headers-`uname -r
it says it is already the newest version.


when i type this: sudo apt-get install build-essential'

it says couldnt find package build-essential


Edit: to let you know, the computer with ubuntu on it ATM does not have internet.. Thats why im trying to install this driver to get internet.

---

### Post by beezkneez2005 on 2007-03-11
dont meen to bump but i really need to get this goin :(

---

### Post by beezkneez2005 on 2007-03-11
anyone??? please.

---

### Post by beezkneez2005 on 2007-03-11
plz.......

---

### Post by houstonbofh on 2007-03-11
I hate these WiFi problems.  Because you will need to download stuff to make it work, and you need to have it work to download stuff.  Somehow you need an internet connection.  You will need build-essential, and some other stuff you will find as build fails.  My recommendation is to go to [http://ralink.rapla.net/](http://ralink.rapla.net/) and print out the list.  Then go to the local computer store, and find one of these.  They have the best support, and work out of the box.  You are also supporting the vendors that support Linux.

Otherwise, you either need a wired Internet connection, or a WiFi bridge.  You can make it work, but it is far from trivial.  Consider that I am good at this, and I only buy stuff that works in Linux out of the box.  (Right now I have a SMC 2532W-B high powered 802.11b high power PCMCIA card, a Belkin F5D7050 v2000 802.11G USB card, and a Airlink AWLC5025 MIMO PCMCIA card.  I also have a box of Linksys and D-link cards that I don't use.)  My time and sanity have value.

---

### Post by beezkneez2005 on 2007-03-11
but isnt my only problem that i need build essentials/?? how does EVERYONE eLSE get it to work without internet?? this is a wifi connection..

---

### Post by beezkneez2005 on 2007-03-11
oops its NOt a wifi connection.  Im installing an ethernet card... Cord to get to internet, not wireless... im almost done, everything is ok but that one thing.. what do i do

---

### Post by beezkneez2005 on 2007-03-11
Plz.. somone

---

### Post by beezkneez2005 on 2007-03-11
bump

---

### Post by gradedcheese on 2007-03-12
> 
Edit: to let you know, the computer with ubuntu on it ATM does not have internet.. Thats why im trying to install this driver to get internet.


Oh!  Then you need to configure APT to use a CD-ROM for the package source.  You can do that with Synaptic, put in the xubuntu CD-ROM, open Synaptic, go to Settings->Repositories and add the CD-ROM there.  Then just use the synaptic search to install 'build-essential' and anything else you might need.  Normally, apt-get is set up to get the packages from the internet...

---

### Post by beezkneez2005 on 2007-03-12
When i try to add the CD-rom it stays stuck on unmounting cd

---

### Post by orangenick on 2007-03-12
Hi, 

I haven't checked if it works with your wireless, but you might want to take a look at madwifi

They have a list of cards that are compatible.  I finally got my wireless card working with that on Fedora 6 64.

Sorry, I can't be much more help because I don't know very much about Ubuntu /linux.

nick

---

### Post by beezkneez2005 on 2007-03-12
again, this is not wireless ><

---

### Post by Jormanks on 2007-03-12
> **gradedcheese said:**
> Oh!  Then you need to configure APT to use a CD-ROM for the package source.  You can do that with Synaptic, put in the xubuntu CD-ROM, open Synaptic, go to Settings->Repositories and add the CD-ROM there.  Then just use the synaptic search to install 'build-essential' and anything else you might need.  Normally, apt-get is set up to get the packages from the internet...

Could this work in ubuntu 6.10?
The problem I have is with the realtek netcard.... maybe this could get things right?

---

### Post by jinx099 on 2007-03-12
Whats wrong with the default distro driver for the NIC?  I have that same card and it works out of the box.  You shouldnt need to compile the driver.

---

### Post by Jormanks on 2007-03-12
> **jinx099 said:**
> Whats wrong with the default distro driver for the NIC?  I have that same card and it works out of the box.  You shouldnt need to compile the driver.

I don't how to put it but, as I read, i find so many troubles with the wired netcards. Is this normal?
I mean, as I said, some people don't need to configure anything since the installation does its stuff. But other people, like me, been wandering for some help here and there. And i have another netcard, not specifically this one... and if you search a little you'll find there are many other cards with installation issues, not just realtek or NIC...

sorry my bad english

---

### Post by beezkneez2005 on 2007-03-12
idk what you guys are talkin about. i think i have a diff issue.

---

### Post by jinx099 on 2007-03-13
IIRC the driver for the DGE-530T is included in all 2.6.5+ kernels.  

Does the network card show up in System -> Administration -> Networking?

What is the output of "cat /etc/network/interfaces"?

---

