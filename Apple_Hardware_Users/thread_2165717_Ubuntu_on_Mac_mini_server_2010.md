---
title: "Ubuntu on Mac mini server 2010"
date: 2013-08-06
forum: Apple Hardware Users
---

### Post by mateo14 on 2013-08-06
Hi


I have Mac mini server 2010 and I want to install Ubuntu 13.04 on this computer. Can you explain to me how to do it, because this computer doesn't have a superdrive. I tried to use a flash drive, but it didn't work and I had errors like "Missing operating system" or "Booting error". also I have iMac with a superdrive, but I'm not sure if it will be helpful information.

---

### Post by Mk32 on 2013-08-06
I would like to say "use an external USB DVD drive" but I'm not so sure if that is supported. It should be, but I don't know if that is the case. 

You can use [rEFIt]("http://refit.sourceforge.net/") to extend capabilities of the traditional "reboot and hold down option key" menu. 

When you made the flash drive, did you run a command like this: 

```
dd bs=4M if=~/Desktop/ubuntu-13.04-desktop-amd64+mac.iso of=/dev/sdb
```

...or something to that effect? I have done a Ubuntu install flash drive in that manner before and it worked fine. 

Another method, is to use Target Disk Mode, if the hardware supports it. I'm not sure if your iMac has FireWire 400/800 ports.

---

### Post by mateo14 on 2013-08-09
Thanks for all the suggestions


> **Mk32 said:**
> I would like to say "use an external USB DVD drive" but I'm not so sure if that is supported. It should be, but I don't know if that is the case.


In this case it probably is going to work only with Apple USB superdrive external which I don't have right now.


> **Mk32 said:**
> You can use rEFIt to extend capabilities of the traditional "reboot and hold down option key" menu. 


I used rEFIT in the past, but now this project is dead I someone created a better project, but I didn't check it yet.

[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

> **Mk32 said:**
> When you made the flash drive, did you run a command like this: 


```
dd bs=4M if=~/Desktop/ubuntu-13.04-desktop-amd64+mac.iso of=/dev/sdb
```


...or something to that effect? I have done a Ubuntu install flash drive in that manner before and it worked fine..  


I ran a similar command, but it didn't work


> **Mk32 said:**
> Another method, is to use Target Disk Mode, if the hardware supports it. I'm not sure if your iMac has FireWire 400/800 ports.


Before you answered on my post I found a much simpler solution of my problem:


[http://sevenbits.github.io/Mac-Linux-USB-Loader/](http://sevenbits.github.io/Mac-Linux-USB-Loader/)


In my opinion Canonical should add this program into Ubuntu or publish an information about him on their website.

---

