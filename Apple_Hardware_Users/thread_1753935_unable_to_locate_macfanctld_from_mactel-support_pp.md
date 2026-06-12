---
title: "unable to locate macfanctld from mactel-support ppa"
date: 2011-05-09
forum: Apple Hardware Users
---

### Post by a lemming on 2011-05-09
I have installed 64-Bit Ubuntu 11.04 on my Macbook Pro 7,1
Following the instructions from here: [https://help.ubuntu.com/community/MacBookPro7-1/Maverick](https://help.ubuntu.com/community/MacBookPro7-1/Maverick)
under Sensors(temps & fans).

I installed the mactel-support PPA, and I did the modprobe coretemp, and I added coretemp to /etc/modules.

Yet for some reason, when I try to install macfanctld using "sudo apt-get install macfanctld", I get this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package macfanctld

I have done this before using 64-Bit Ubuntu 10.10 on this same laptop and it worked fine.

thanks in advance.

---

### Post by samuaz on 2011-05-09
install it manual copy and ejecute in terminal:

```
wget http://ppa.launchpad.net/mactel-support/ppa/ubuntu/pool/main/m/macfanctld/macfanctld_0.5~mactel1~maverick_amd64.deb
sudo dpkg -i macfanctld_0.5~mactel1~maverick_amd64.deb
```

---

### Post by jerrycal on 2011-05-12
> **a lemming said:**
> I have installed 64-Bit Ubuntu 11.04 on my Macbook Pro 7,1
Following the instructions from here: [https://help.ubuntu.com/community/MacBookPro7-1/Maverick](https://help.ubuntu.com/community/MacBookPro7-1/Maverick)
under Sensors(temps & fans).

I installed the mactel-support PPA, and I did the modprobe coretemp, and I added coretemp to /etc/modules.

Yet for some reason, when I try to install macfanctld using "sudo apt-get install macfanctld", I get this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package macfanctld

I have done this before using 64-Bit Ubuntu 10.10 on this same laptop and it worked fine.

thanks in advance.


I added the Maverick repo and was able to get the applesmc and macfanctld...

---

### Post by a lemming on 2011-05-13
Thanks guys, I got it working :)

---

### Post by SwedishWings on 2011-08-18
Sorry for the delay. macfanctld is now available from mactel PPA.

/Mike

---

### Post by SlothsAreEverywhere on 2011-11-19
Thanks a lot ! I've been struggling with this for a long time !

---

### Post by nicholas on 2012-04-07
> **SwedishWings said:**
> Sorry for the delay. macfanctld is now available from mactel PPA.

/Mike

Hi, will you you be updating the Mactel PPA for 12.04?

---

### Post by SwedishWings on 2012-04-21
I've made macfanctld available for Oneiric on the PPA. Will make it available for Precise when the mactel PPA supports it.

Sorry for the delay, been drowning in work and private issues for a while. Hopefully the situation will improve soon.

/Mike

---

### Post by SwedishWings on 2012-04-21
I finally got around to check up the reported high CPU usage. 

It turned out that;
- sprintf() is an expensive operation that should be avoided.
- fopen()/fclose() are CPU hogs. Have been replaced with open()/close().

The above changes should decrease the CPU usage dramatically. 

Please test the new version for Oneiric. A Natty version is building now, should be available in a few hours.

/Mike

---

### Post by SwedishWings on 2012-04-22
> **nicholas said:**
> Hi, will you you be updating the Mactel PPA for 12.04?

It's in the Precise mactel PPA now. Please let me know if it's ok!

/Mike

---

### Post by jameh on 2012-07-18
I installed macfanctld_0.5~mactel1~maverick_amd64 on my Macbook Pro 5,1 running 64-bit Ubuntu Studio 12.04, and my fans are running / being regulated now!

---

