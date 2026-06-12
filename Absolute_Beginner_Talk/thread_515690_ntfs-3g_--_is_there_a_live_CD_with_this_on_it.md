---
title: "ntfs-3g -- is there a live CD with this on it?"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-08-02
Is there a live CD with ntfs-3g on it?  The reason I would like this is to be able to fix a Windows OS by restoring a corrupted file.

Carl

---

### Post by Acglaphotis on 2007-08-02
I think linux mint has one.

---

### Post by taurus on 2007-08-02
I recall the latest version of Knoppix comes with it too.

---

### Post by LaRoza on 2007-08-02
Slax Kill-bill Edition has all Windowsy stuff on it, Wine, ntfs-3g, etc.

[www.slax.org](www.slax.org)

---

### Post by thefoolisme on 2007-08-02
ubuntu Ultimate has it on there too.  was a lifesaver for me when I had to sift through a corrupt XP drive.  :-)

---

### Post by ugm6hr on 2007-08-02
I think the GParted LiveCD has it too.

---

### Post by LaRoza on 2007-08-02
> **ugm6hr said:**
> I think the GParted LiveCD has it too.

It does.

---

### Post by fastpakr on 2007-08-02
Assuming you have internet access, can't you also just apt-get it after booting?

---

### Post by AnRa on 2007-08-02
[System Rescue CD](http://www.sysresccd.org/) ;)

---

### Post by Hospadar on 2007-08-02
If you have an internet connection you can install this after booting with the live cd from synaptic (it won't actually put anything on you hdd, it just adds it to the temp. filesystem in memory), and if you don't have a net connection, you can always manually download the .deb file and then put in on a flash drive or cd, and then install it by double-clicking it

---

### Post by cwmoser on 2007-08-02
FYI, this is what I had to do.

I was wanting to fix a corrupted file on a PC that would not boot.  It was on a Windows domain.

I booted Ubuntu Ultimate and got a dynamic IP address but since the security there would not allow Internet access unless you joined the domain, I had to circumvent the security by establishing a static IP and setting the gateway to a special address to bypass the Proxy Server -- something like this:

ifconfig  eth0 down
ifconfig  eth0  192.168.0.33  netmask  255.255.255.0  up
route add default gw 192.168.0.201  eth0

This made the IP static and set the gateway and was the only way to get to the Internet.

The reason was I needed access to the Internet so apt-get could do its work.  Then I installed ntfs-3g like this:

sudo  apt-get  update
sudo  apt-get  install  ntfs-3g


Once ntfs-3g was installed, I mounted the NTFS partition as R/W via:

sudo mkdir /media/disk
sudo mount  -t  ntfs-3g  /dev/sda1  /media/disk

Carl

---

