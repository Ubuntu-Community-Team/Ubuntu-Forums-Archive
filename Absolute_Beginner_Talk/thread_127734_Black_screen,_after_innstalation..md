---
title: "Black screen, after innstalation."
date: 2006-02-09
forum: Absolute Beginner Talk
---

### Post by KrE on 2006-02-09
Hi, pardon my english(im from Norway ;) ).
I have innstaled Ubuntu 5.10, the instalation works well,
but when it is finished the screen goes black. 
Even though the computer is on and running.
What may be the problem? :-k 
Is it the graphiccard/videocard?(It`s bold in the setup list, asus.)

This is my setup:
AMD Athlon 64 3200+ 2.0 GHz Socket 939
Corsair TWINX1024-3200XL DDR-DIMM 1024MBKit
NEC DVD recorder ND-3500A IDE
SMC EZ Connect Wireless G PCI 54 Mbps 802.11g/b
EPoX EP-9NDA3+ Hovedkort for S939 nForce3
**Asus V9999 GeForce 6800 128MB DDR AGP, TV-Out, DVI, Retail**
Seagate Barracuda 7200.7 200GB S-ATA 8MB cache 7200RPM

Thanks Erlend.

---

### Post by Mustard on 2006-02-09
Can you get to a command line by hitting ctrl + alt + f1 ?

If you can get to a command line, or login prompt and log in with your username and password, you could try entering this command..

```
sudo dpkg-reconfigure xserver-xorg
```

It will bring up a dialog, for which you can choose the default answers in most cases, but when it comes to the choice of graphics card drivers, you could choose 'vesa'.  I'm assuming its currently set to 'nv' or 'nvidia'.  When you finish the dialog you can try to start the x server again, by typing..

```
startx
```

---

### Post by KrE on 2006-02-11
Thank you, I will try this.
:)

---

