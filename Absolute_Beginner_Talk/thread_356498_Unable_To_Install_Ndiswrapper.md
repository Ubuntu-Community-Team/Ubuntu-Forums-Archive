---
title: "Unable To Install Ndiswrapper"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by username132 on 2007-02-08
Trying Ubuntu via liveDVD and need to set up my wireless card driver using ndiswrapper. Trying to follow the instructions here: [http://www.das-werkstatt.com/forum/werkstatt/viewtopic.php?t=415&highlight=wireless](http://www.das-werkstatt.com/forum/werkstatt/viewtopic.php?t=415&highlight=wireless)

My computer connects wirelessly to the internet via Windows XP so I must download the packages manually to a USB drive to test them later with LiveDVD:

ndiswrapper-utils (1.8-0ubuntu2)
ndiswrapper-common (1.18-1ubuntu2)

One of these installs successfully using the GUI where as the other says:
"Error: dependancy not satisfiable - libc6

I found libc6:
libc6_2.3.6-0ubuntu20_amd64.deb

In the GUI it says it's the same version as already installed. Installing it again makes no difference. Is it because I'm running it straight from the DVD without installing?

Please advise.

---

### Post by aysiu on 2007-02-09
ndiswrapper is on the Ubuntu CD, actually: ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install ndiswrapper-utils
``` should do the trick.

---

