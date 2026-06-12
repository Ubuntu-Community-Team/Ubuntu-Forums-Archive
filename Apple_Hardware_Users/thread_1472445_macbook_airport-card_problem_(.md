---
title: "macbook airport-card problem :("
date: 2010-05-04
forum: Apple Hardware Users
---

### Post by deniselechner on 2010-05-04
Hello Community,

I'm really sorry for the (stupid) - 100 times answered - question. I've been using mac osx since a long long time and few hours ago I decided to install ubuntu 9.10. I'am using ubuntu since a year in the virtual box. And now I formatted my harddisk.

So, my problem - as i wrote in the headline - is the airport card. With Ethernet i am able to connect to the internet. i found a package in a familiar forum which was called "ndiswrapper" but it doesn't work really well. the process plummet while it was running.

I also read a version in which they wrote to go to System > Administration > Hardware Drivers but the page are blank. "No proprietary drivers are in use on this system."

Are there any useful drivers to use?

Thanks for your help
best regards 
denise lechner

---

### Post by linuxopjemac on 2010-05-04
what kind of network card do you have? Maybe better question, what is your exact Mac model ?

---

### Post by deniselechner on 2010-05-05
> **linuxopjemac said:**
> what kind of network card do you have? Maybe better question, what is your exact Mac model ?

Hello Linuxopjemac,

The Problem solved itself.
I have a MacBook 3,1 und found a command for the terminal to install those packages. With the Terminal it doesn't work well. After a while i found what i was looking for in the synaptic package mangager.

thx.
Denise Lechner

---

### Post by linuxopjemac on 2010-05-05
good that you solved the problem. Can you make change this post to SOLVED please?

---

### Post by mixmac38 on 2010-05-13
I have the same MacBook model and the same problem, can you please tell me what terminal commands you used to get the airport working?

---

### Post by linuxopjemac on 2010-05-13
be sure to be connected with internet with a cable, then

```
sudo apt-get update
sudo apt-get upgrade
```

Then go to System -> Administration -> Hardware drivers

Hopefully you can then enable the Broadcom wireless driver

---

