---
title: "cant see my hard disks"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by sidslasttheorem on 2007-01-28
hey!,
 i downloaded the .iso file for desktop from a torrent & wrote it onto a cd.
When i boot from the cd however, i cant access my hard disks.... but i can see the partitions and stuff when i run GParted... 
  Is this because i havent actually installed Ubuntu yet onto my desktop, or is there something is should do..?
 
any help much appreciated :D
 thanks!

---

### Post by taurus on 2007-01-28
It is because you haven't mounted your harddrives.  You need to mount them before you can access them.  Do you plan to install Ubuntu on your machine?

---

### Post by sidslasttheorem on 2007-01-28
hey!
 yes i most probably will install it on my system, 
i've gotten bored of playing around in windows & my cousin suggested Ubuntu to me.
ive got some previous with Mepis though...
 btw, how exactly do i mount my hard disks & also how do i set up my internet connection(broadband) ?

as before... any help, much appreciated... :D

---

### Post by highneko on 2007-01-28
When you install the ubuntu desktop onto your hdd it asks you what path to mount the filesystem when it boots. It can't mount automatically on a livecd because you can't install onto a mounted filesystem. You can mount the filesystem but then you couldn't install ubuntu on it.

To mount manually open a terminal and type something like:

# first make the directory
sudo mkdir /example
# to mount the first parittion on a pata hdd
sudo mount /dev/hda1 /example

---

### Post by taurus on 2007-01-28
Install Ubuntu first and worry about mounting Windows partitions later after you have a working machine.

---

### Post by sidslasttheorem on 2007-01-28
oh yes, i understood that part... im now going to create a separate partition on my main disk (80 gb - split as c:40, d:20, e:20... and im going to further split c: into 20+20 and install Ubuntu onto that), but my query is whether i can access my hard disks & internet & stuff without actually installing it?

---

### Post by taurus on 2007-01-28
Can you surf the net with firefox from the LiveCD?

---

### Post by sidslasttheorem on 2007-01-28
i can access firefox but i dont know how to setup the internet connection from the boot cd... if its possible....

---

### Post by taurus on 2007-01-28
Open a terminal and see what happens when you run this command?

Applications -> Accessories -> Terminal
```
ping -w 3 www.yahoo.com
```

---

### Post by sidslasttheorem on 2007-01-28
thanks, but could you also tell me the stuff to do to mount my hard disks... im on windows & ill have to reboot to get into Ubuntu... so id like to collect all the info required... :D
...with regard to the "ping -w 3 www.yahoo.com" ... i remember i clicked a online help file or something which in turn opened firefox with the "cannot find page" thing...

---

### Post by taurus on 2007-01-28
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by sidslasttheorem on 2007-01-28
thanks a lot... !!

---

### Post by Pobega on 2007-01-28
You can access your hard discs. You'll have to know what device it is, though. In my case my HDD shows up as /dev/sda, so from a LiveCD I can just mount it using> mkdir /mnt/root
mount -t auto /dev/sda1 /mnt/rootYour system most likely won't be the same thing, though. so you can use gparted to figure out what devices your computer is picking up automatically.

---

### Post by highneko on 2007-01-28
> **sidslasttheorem said:**
> i can access firefox but i dont know how to setup the internet connection from the boot cd... if its possible....

Wired connection? Wireless? Router? We might need some actual information. Try "ifconfig" from a terminal and paste the output.

---

### Post by sidslasttheorem on 2007-01-28
in gparted, i see this hda(3 partitions) & hdb(single partition).....

---

### Post by sidslasttheorem on 2007-01-28
my connection is a usb wired broadband connection (Airtel India is the isp)... connects via ADSL splitter from phone line....

---

