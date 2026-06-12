---
title: "Where is 'make'"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by John E on 2006-11-29
Now that I'm starting to install the more esoteric hardware on my system (e.g. my broadband modem) I noticed that quite a few of the scripts require **make**. As far as I can tell, **make** wasn't installed on my system. Should it be there? If not, how do I get it?

---

### Post by Super King on 2006-11-29
Yup, just install the *make* package from Synaptic Package Manager (or using the command sudo apt-get make).

---

### Post by linear on 2006-11-29
It's better to install **build-essential**. (Get everything you may need.)

---

### Post by John E on 2006-11-29
> **Super King said:**
> (or using the command sudo apt-get make).

Won't that require me to already have internet access? It's the internet access that I'm trying to get working. :confused:

---

### Post by taurus on 2006-11-29
Package build-essential is on the installing CD so insert the CD, open a terminal, Applications -> Accessories -> Terminal, and type

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by IncomingFire on 2006-11-29
You could d/l the .deb from [here]("http://archive.ubuntu.com/ubuntu/pool/main/b/build-essential/") on another computer and usb drive/cd/dvd/floppy it over to the computer you are installing on.

---

### Post by John E on 2006-11-29
Thanks guys. I'll give it a try.

---

### Post by Ashtarot on 2006-11-29
i dont think u need to do that much to configure your network,just connect your pc to internet,then configure the network seetings from the GUI interface

system -> administration -> networking

That way ul get acces to internet, in my case im conected by cable, and my pc is always conected so i was able to have acces to internet since i was installing ubuntu from the live cd, if u have a wireless modem u have to configure the wireless network from the gui interface, its rather easy..... give it a try.

Once are done with it u can use the apt-get build-essential 
command

---

### Post by John E on 2006-11-29
Thanks. My specific problem is that I'm using a Speedtouch 330 broadband modem whose drivers aren't installed by default.

Incidentally, the article I read suggested that **build-essential** included various things like **g++** for example. However, that didn't get installed for me.... :(

---

### Post by 56phil on 2006-11-29
How do you connect you modem to your computer?

---

### Post by John E on 2006-11-30
**56phil** - It's a USB modem.

---

