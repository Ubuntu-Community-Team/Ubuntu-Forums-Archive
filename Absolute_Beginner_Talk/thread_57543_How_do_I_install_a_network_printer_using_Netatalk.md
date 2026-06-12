---
title: "How do I install a network printer using Netatalk?"
date: 2005-08-16
forum: Absolute Beginner Talk
---

### Post by newtoubuntu2 on 2005-08-16
I am trying to run Ubuntu on a network that has only Appletalk printers.  I used Synaptic to install Netatalk.  I'm unsure as to how to proceed from there to install a network printer and make it my default printer so that I can print easily from within OpenOffice.  Any input would be appreciated.

---

### Post by mneptok on 2005-08-28
I just wrote up a how-to on this subject on the Ubuntu wiki. Have a look [here](https://wiki.ubuntu.com/AppleTalk).

HTH.

---

### Post by newtoubuntu2 on 2005-08-29
Works like a charm!  Thanks for the detailed advice.  That's exactly what I needed.

---

### Post by jamescoy on 2007-06-30
I tried this but could not get the name of my printer:

james@james-desktop:~$ sudo apt-get install netatalk
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
netatalk is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
james@james-desktop:~$ nbplkup
                  james-desktop:AFPServer                          65280.16:128
                  james-desktop:netatalk                           65280.16:4
                  james-desktop:Workstation                        65280.16:4

Where would I go from here?

Thanks.

---

