---
title: "Opening Ports"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by JacenMandarin on 2007-07-04
I'm trying to get Azureus working properly. It's downloading, but the rate isn't fantastic. I've set up a static IP and the ports are open on my router. According to azureus' site, all the ports are closed by default with Ubuntu. It gives some instructions on how to open them but I don't think I've done it right. I even installed firestarter and thought I had them opened through it but Azureus still says it's firewalled. Can someone please give me some thorough instructions on what to do? I've searched the forum but none of the answers have been very helpful. I'm really an absolute beginner here and need someone to tell me exactly what to do if they can. Thankyou in advance.

---

### Post by brennydoogles on 2007-07-04
> **JacenMandarin said:**
> I'm trying to get Azureus working properly. It's downloading, but the rate isn't fantastic. I've set up a static IP and the ports are open on my router. According to azureus' site, all the ports are closed by default with Ubuntu. It gives some instructions on how to open them but I don't think I've done it right. I even installed firestarter and thought I had them opened through it but Azureus still says it's firewalled. Can someone please give me some thorough instructions on what to do? I've searched the forum but none of the answers have been very helpful. I'm really an absolute beginner here and need someone to tell me exactly what to do if they can. Thankyou in advance.

If your router has UPNP enabled Azureus can open the ports for you and forward them as well. Have you tried that??

---

### Post by atria on 2007-07-04
I am almost 100% positive that Ubuntu does not ship with a firewall by default, that is, the port azureus uses should not be blocked.

If the NAT tester in Azureus says that you're behind a NAT, chances are that your router is not configured properly. In this case you'll have to setup port forwarding so that the ports can be opened. In other words your router is acting like a firewall and needs to be configured and hence having nothing to do with ubuntu.

Heres a simple tutorial on port forwarding: [http://portforward.com/routers.htm](http://portforward.com/routers.htm)

However if Azureus says that the port is correctly opened/forwarded and you're still getting crap download speeds, then there is nothing you can do about it since the problem is likely to be due to the torrent itself.

---

### Post by JacenMandarin on 2007-07-04
No, like I said, I've done all that. Seems that I just figured out my own problem though. I restarted the comp, just to see if that would help and now my NAT problems are gone. Speeds are up, the worlds still turning etc. etc. Sorry to be a bother. There really should be some documentation on this though. I've searched and searched but haven't found anything definitive. Just lots of people asking the same questions. :)

---

### Post by qamelian on 2007-07-04
> **atria said:**
> I am almost 100% positive that Ubuntu does not ship with a firewall by default, that is, the port azureus uses should not be blocked.

Ubuntu ships with iptables installed by default, so, yes, Ubuntu does have a firewall automatically in place. Many people refer to Firestarter as a firewall, but it isn't. Firestarter is only a graphical front-end to iptables.

---

### Post by HotShotDJ on 2007-07-04
> **atria said:**
> I am almost 100% positive that Ubuntu does not ship with a firewall by default, that is, the port azureus uses should not be blocked.Absolutely incorrect.  The firewall in Linux (including Ubuntu) is iptables which is built into the kernel -- with Ubuntu, all ports are closed by default.  Firestarter is NOT a firewall... it is simply a GUI interface to iptables.

---

### Post by atria on 2007-07-04
Woot, glad it works now ;) 
In any case i think it might be because your router did not register your computer properly. In that case, a
```
sudo /etc/init.d/networking restart
```
should fix the problem too.

---

### Post by atria on 2007-07-04
Ubuntu ships with a firewall, but it is not enabled by default. Unused ports are closed, but if a program like azureus binds to a port, the port does not get blocked.

Do a sudo iptables -L after a clean installation and you'll see.

---

### Post by JacenMandarin on 2007-07-04
Firestarter really helped. I just wish I had some more docs on it. That and I wish it told me that I needed to restart. Ah well, a friend just told me that most system config changes only load at startup. I guess I'm just used to having windows tell me to do it. :P I really do love this little os though. It's fun. ^^

---

### Post by atria on 2007-07-04
I'm not sure if firestarter policies/rules are put into place automatically after implementing a change, but i'm positive that you can restart the firewall without restarting your computer by using this command:

```
sudo /etc/init.d/firestarter restart
```

---

