---
title: "dell Truemobile 1150 card question"
date: 2011-04-18
forum: Any Other OS
---

### Post by pythonsyntax on 2011-04-18
Well here m y prob.I got my wireless dell TrueMobile 1150 series pc card it work good in sabayon but in ubuntu 10.10 Why is that?And how would i get it to work in ubuntu?

---

### Post by pythonsyntax on 2011-04-18
anyone?

---

### Post by TBABill on 2011-04-18
Sabayon comes with non-free drivers by default. Ubuntu does as well, but they must be activated differently. Once you get to the desktop from a LiveCD (or from an installed Ubuntu), go to System>>Administration>>Hardware (or Additional Drivers) and let the system find your device. If it offers you a proprietary driver to install, just click through the steps until it installs and restart. If you want it working from the LiveCD, however, instead of restarting you need to do a ```
sudo modprobe nameofyourdriverhere
``` Example: My Broadcom BCM4312 CAN run from the live session without plugging into a router. I just follow the steps I outlined for you above, choose the right driver, let it install (from the CD or DVD) and when it tells me to restart, then instead of restarting I just ```
sudo modprobe wl
``` where "wl" is the name of the driver my card uses. I wait a few moments and then my wireless connections are available.

---

### Post by pythonsyntax on 2011-04-18
what driver would i need to make sure it works?

---

### Post by pythonsyntax on 2011-04-18
Anyone?

---

### Post by pythonsyntax on 2011-04-19
i try to have the propierary and couldn't find the driver?

---

### Post by pythonsyntax on 2011-05-12
You mean sudo modprobe Orinoco_cs?

---

### Post by Nemontemi on 2011-10-11
I have the same problem, have you found a solution?

---

### Post by pythonsyntax on 2011-11-12
Nope i have not found anything on it yet.

---

