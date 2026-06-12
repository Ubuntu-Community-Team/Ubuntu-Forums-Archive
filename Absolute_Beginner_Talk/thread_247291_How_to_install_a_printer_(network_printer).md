---
title: "How to install a printer (network printer)"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by A dreamer on 2006-08-30
Hi,
Maybe someone could give me an advice?
I'm new to Linux, but have managed to install Ubuntu, updated it, installed drivers for NVIDIA, etc, but I'm not able to install my network printer.
I have a small home network (6 PC's and a couple of NAS) and a HP Deskjet 5850 connected to the network via WLAN.
I found a manual "how to..." at ...hp.com and followed it in every detail. 
All stopped when I had to access a web address "http://localhost:631". IN the manual they say that I should use root and root password, but on the "Cups" site they ask for user and password for Cups, what is correct.
Have tried to register me as a user at CUps, but it did not help.
So, is there anyone who could give a hint on how to proceed?

BR,
A dreamer

---

### Post by jjf on 2006-08-30
I tried much the same thing you did (with a Brother printer on a network), and did enough reading to conclude that CUPS was more or less broken.  Instead, I followed the guide here:

[http://ubuntuguide.org/wiki/Dapper#Print_Server_.28cupsd.29](http://ubuntuguide.org/wiki/Dapper#Print_Server_.28cupsd.29)

and was able to get my networked printer working, albeit with a "second best" driver.

---

### Post by A dreamer on 2006-08-30
Hi,
Thanks a lot for your proposal.
I tried it, but it did not work. When I made the cmd "lpq" I got the answer "cannot connect to the server"

I wonder if you or someone have some other proposal I could try?

in advance, thanks a lot
/A dreamer

---

### Post by PPAAUULL on 2006-08-30
I installed a network printer, not using CUPS but using the KDE printer setup tool. It seemed to work after I got the right driver and everything. I don't know if you are running KDE but if you are then you can try that.

---

