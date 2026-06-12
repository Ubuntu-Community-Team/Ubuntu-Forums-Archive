---
title: "Firestarter question"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by fasoulas on 2006-11-12
HOW can i make firestarter start at start up?????

And does firestarter really helps protect me pc...

---

### Post by aidanr on 2006-11-12
firestarter is just a gui frontend to iptables
if you want it to startup automatically

```
sudo visudo
```
change the line that says
```
%admin ALL=(ALL) ALL
```
to
```
%admin ALL=(ALL) ALL, NOPASSWD: /usr/sbin/firestarter
```
save and exit and go to

System->Preferences->Sessions->Startup Programs

hit "Add" and type in 
```
sudo firestarter --start-hidden
```
hit ok and close

---

### Post by HereInOz on 2006-11-12
In case you are wondering, IPTables, for which Firestarter is a GUI front end, does start on boot up of Ubuntu.  IPTables is a firewall which will add to the security of your computer, especially if this particular computer is directly connected to the Internet, rather than via a NAT router.  It protects you against uninvited access to your computer from the Internet.

So the IPTables firewall loads at start up anyway, even though Firestarter does not.  If this is all you need to know, that is fine, but if it is specifically Firestarter that you need to have running at start up, then the instructions above show you how.

---

### Post by kinematic on 2006-11-12
uhmmm....don't know why it doesn't start on boot for you but it does for me....didn't have to configure anything.

---

### Post by HereInOz on 2006-11-12
Mysteries of the Quantum Universe!! :-)

---

