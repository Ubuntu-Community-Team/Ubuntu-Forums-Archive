---
title: "Simple HDD Question"
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by BitTorrentBuddha on 2006-02-16
is it possible to just add the space from a slaved hdd too the space on the master hdd (i.e. my 120gb drive is slaved to my 30gb)? I'm assuming it's probably automatic, but I'm not sure. I would like to know before I buy another hdd. Thanks

---

### Post by psusi on 2006-02-16
Unless you formatted the drive with LVM, then no.  

You can mount the new hard drive as your /home directory though, and keep all your bulk storage there, and the rest of the system on the old drive.

---

### Post by BitTorrentBuddha on 2006-02-16
so there's no way for it to just read 150gb?

---

### Post by BitTorrentBuddha on 2006-02-17
bump :(

---

### Post by BitTorrentBuddha on 2006-02-17
which drive would I have to format with LVM and can I do that and retain the data I have?

---

### Post by patrick295767 on 2006-02-17
(that's a very interesting post, I hope u'll have more replies about it)... Greetz'

---

### Post by BitTorrentBuddha on 2006-02-17
bump, really want to get a new hdd but I need to know this first :(

---

### Post by David Corrales on 2006-02-18
You'll probably have to backup then format all drives with LVM (Logical Volume Manager). Then yeah, you'll just read 150gb and so on as you add more drives.

---

### Post by patrick295767 on 2006-02-18
Good web site about the LVM:
[http://www.tldp.org/HOWTO/LVM-HOWTO/]("http://www.tldp.org/HOWTO/LVM-HOWTO/")
 
Let us know if you made it 

Greetz

---

### Post by BitTorrentBuddha on 2006-02-18
I'm not sure if I remember correctly, but format with LVM was an option on the ubuntu install disk, right?

---

### Post by Rizado on 2006-02-18
Why don't you just mount the new one as /home or something? It's never healthy to have one big drive. Partition it.

---

### Post by BitTorrentBuddha on 2006-02-18
so, I could keep all my packages and system on the 30 gigger and put the mass storage on the 120 and still be able to use the packages from the 30 gigger?

---

### Post by patrick295767 on 2006-02-19
[QUOTE=BitTorrentBuddha]so, I could keep all my packages and system on the 30 gigger and put the mass storage on the 120 and still be able to use the packages from the 30 gigger?[/QUOTE]
  
In my case, I have a Linux SERVER. 20 GB for the SERVER and 160GB of storage for  the 3 other PC's of the network. I can then have exactly exactly same session on every pc of the network. U may work on any pc and ur session & data are identical.
   
The idea is to automatically do : ```
mount -t nfs server:/mnt/homestorage  /home 
```
when the PC starts up.
  
The prob is in ur case 30GB is rather too much. U loose about 15GB for nothg (cos the linux system is very small : few gb).

Greetz

Patrick

---

### Post by BitTorrentBuddha on 2006-02-19
yeah, but 120gb, maybe more considering some deals I've found recently, should be enough for me, and if having it all as one big partition would be bad then I wouldn't have a problem losing 15gb. I just want to know if I can keep all the packages and system upgrades on one hdd and if I can how can I assign updates to go to the smaller drive? or would mounting it as /home just automatically put all files in my home directories on that drive? and if that's the case will the files currently under my /home directory automatically be moved?

---

### Post by BitTorrentBuddha on 2006-02-20
baby bump

---

### Post by BitTorrentBuddha on 2006-02-21
shameless bump :(

---

### Post by BitTorrentBuddha on 2006-02-23
whoriest bump ev-ar

---

