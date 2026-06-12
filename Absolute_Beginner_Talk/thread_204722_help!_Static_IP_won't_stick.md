---
title: "help! Static IP won't stick"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by PixelPixie on 2006-06-27
I'm new to linux and installed Ubuntu 6.06 desktop on a machine I'm planning to use as a web server.

I have a host name, static IP address, gateway, DNS server addresses, and subnet mask.  I enetered those numbers under System>Administration>Networking for the Ethernet connection.

The machine can't ping other machines or see web pages.  And if I ping this machine I get a timeout error (also can't use ssh or remote desktop, see its home page, etc etc).

Someone told me to run route -n, and it gives Gateway 0.0.0.0 and the wrong destination and Genmask.

Help?? :confused:

---

### Post by MaximB on 2006-06-27
after you enter thouse number - are/when do they return to default ?
after 10-20 min ??? can you go online for 10 min and then disconect ???

---

### Post by PixelPixie on 2006-06-27
They don't ever return to default. The Network Settings window always looks like the correct addresses are entered, but the computer won't connect at all.

---

### Post by MaximB on 2006-06-27
did you even installed your adsl modem (I hope you use it - cuz it's the only one I have exp. with) ?

---

### Post by PixelPixie on 2006-06-29
For some reason in the network settings the default gateway wasn't selected.  That fixed the problem.

---

