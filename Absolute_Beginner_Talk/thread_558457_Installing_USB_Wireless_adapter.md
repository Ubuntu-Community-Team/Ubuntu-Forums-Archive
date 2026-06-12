---
title: "Installing USB Wireless adapter"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by Gerry Mann on 2007-09-24
I have two USB adapters Airlink AWLL3026, zydas chip, and AWLL 5026, ralink tech chip,. I have tried to download both 1.47 and 1.8 versions of ndis... without success. I get errors that say, file is not in gzip format when I use the tar -zxvf -ndiswrapper-1.8.tar.gz command. A friend and trouble shooting guides have suggested i install ndisgtk and that does not seem to be in my, ALT Ubuntu 6.06 LTS versioin of Ubuntu. I have both the windows and Linux drivers for these adapters, however I don't know how to proceed. Any help would be greatly appreciated.

---

### Post by LowSky on 2007-09-24
Go into System>Admin>Synaptic Pakage Manager and install ndiswrapper from there...

---

### Post by overdrank on 2007-09-24
> **Gerry Mann said:**
> I have two USB adapters Airlink AWLL3026, zydas chip, and AWLL 5026, ralink tech chip,. I have tried to download both 1.47 and 1.8 versions of ndis... without success. I get errors that say, file is not in gzip format when I use the tar -zxvf -ndiswrapper-1.8.tar.gz command. A friend and trouble shooting guides have suggested i install ndisgtk and that does not seem to be in my, ALT Ubuntu 6.06 LTS versioin of Ubuntu. I have both the windows and Linux drivers for these adapters, however I don't know how to proceed. Any help would be greatly appreciated.

Hi have you installed build-essential also? :(

---

### Post by Gerry Mann on 2007-09-24
I went into Synaptic Package manager and searched for ndiswrapper and it said:
Linux-image-2.6.15-26-386... etc ...  is installed.
how do I use this to launch the 1.8version of ndiswrapper?

Secondly when i tried to install build-essentials, with sudo apt-get install build-essential, it said:
Package build-essential is not available .... etc
E: Package build-essential has no installation candidate.

---

### Post by Gerry Mann on 2007-09-24
Well. It seems that I needed to conncet hard wire to the network and recieve 164 updates. Then I can start some of the instructions offered. I will retur and post my results after I get some.

---

