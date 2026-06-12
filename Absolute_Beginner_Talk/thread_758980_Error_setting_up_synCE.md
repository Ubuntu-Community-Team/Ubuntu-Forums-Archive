---
title: "Error setting up synCE"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by knottshawk on 2008-04-18
I'm going thru the instructions at [www.synce.org/moin/SynceWithUbuntu](www.synce.org/moin/SynceWithUbuntu) and when I get to the part where I'm supposed to enter: sudo apt-get install usb-rndis-source cdbs I get a response saying "Package cdbs is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only availble from another source" "E: Package cdbs has no installation candidate"

What did I do wrong.... all I want is to sync my pda!

---

### Post by unutbu on 2008-04-18
```
% apt-cache policy cdbs
cdbs:
  Installed: (none)
  Candidate: 0.4.49ubuntu2
  Version table:
     0.4.49ubuntu2 0
        500 http://archive.ubuntu.com gutsy/main Packages

```

Therefore, it appears you need 

```
deb http://archive.ubuntu.com/ubuntu gutsy universe multiverse restricted main
```

in your /etc/apt/sources.list. (You only need main, not universe multiverse and restricted, so feel free to remove those if you wish.)

Then run 

```
sudo apt-get update
sudo apt-get install cdbs

```

---

### Post by knottshawk on 2008-04-18
I suspect now I have a bigger problem. I think one of the previous commands disabled my usb.... and .... USB is what I use to connect to my router. So, now I have no internet.

---

### Post by unutbu on 2008-04-18
I'm sorry to hear you're having problems with USB, but any knowledgeable reader of this thread should be able to assure you that the commands suggested above can in no way disable your USB.

---

### Post by knottshawk on 2008-04-18
How about these commands? They came before the ones I'm asking for help with...

sudo rmmod rndis_host cdc_ether usbnet

sudo rm /lib/modules/`uname -r`/kernel/drivers/net/usb/{rndis_host,cdc_ether,usbnet}.ko

---

### Post by unutbu on 2008-04-18
Yep, that might bork your usb.

---

