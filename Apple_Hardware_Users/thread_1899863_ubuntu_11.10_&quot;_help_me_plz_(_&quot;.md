---
title: "ubuntu 11.10 &quot; help me plz :( &quot;"
date: 2011-12-24
forum: Apple Hardware Users
---

### Post by mohamedmak on 2011-12-24
Hi guys, 
I'm kinda new to linux world (ubuntu). I bought a macbook pro 7.1 and i've installed ubuntu 11.10 on it, but I found some problems with the hardware compatability :( In ubuntu's additional drivers I couldn't find any driver detected :( my nvidia is not detected too :(
please help me ^^

---

### Post by Apewall on 2011-12-25
sudo apt-get install nvidia-current

what other drivers were missing?

---

### Post by BC59 on 2011-12-25
> **mohamedmak said:**
> Hi guys, 
I'm kinda new to linux world (ubuntu). I bought a macbook pro 7.1 and i've installed ubuntu 11.10 on it, but I found some problems with the hardware compatability :( In ubuntu's additional drivers I couldn't find any driver detected :( my nvidia is not detected too :(
please help me ^^

If you cannot install the NVIDIA drivers from the **Additional Drivers** application, install them through the ppa, run this from a terminal CTRL+ALT+T (it's similar to the comment of @Apewall):

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings

```

---

### Post by mohamedmak on 2011-12-26
One more thing is the temperature of the the laptop .. I think the cpu's temperature goes hot quickly or something like that !!! idk if this is true or?? :/

---

### Post by BC59 on 2011-12-26
It's connected with the installation of the drivers.

---

### Post by lothur on 2011-12-27
I have the same problem with high cpu and temperature. This was not an issue on 10.04 - 11.04, but 11.10 is crap on macbook pro 7-1. I'm still hoping for a fix on this problem.

---

