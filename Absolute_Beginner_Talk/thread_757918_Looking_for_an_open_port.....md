---
title: "Looking for an open port...."
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by Fatal Equinox on 2008-04-17
How would I find an already open port?

I have checked the forum and found bunch of useful stuff on opening ports, but all i think i really need is to find an open port.. im using Azureus and it seems that the tcp port its listening to keeps timing out (either busy or closed port).   Should i just try and opening it or should i just do like i figured and find a open one?


Thanks in advance....

---

### Post by Moop on 2008-04-17
It depends on how you're connected to the internet. If your behind a router then you open the port on the router using the routers configuration utility. I don't think Ubuntu would by default block Azureus.

---

### Post by TeoBigusGeekus on 2008-04-17
> **Moop said:**
> I don't think Ubuntu would by default block Azureus.
Unless you have a firewall install (Firestarter for example)...

---

### Post by Fatal Equinox on 2008-04-17
> **Moop said:**
> It depends on how you're connected to the internet. If your behind a router then you open the port on the router using the routers configuration utility. I don't think Ubuntu would by default block Azureus.

Ah!!!,,,  I see gotta do it thorugh the router and modem..... ok.... though isn't their a command through the terminal to look for a open port?   like i know there is in windows,,,, just don't know my way through linux yet... :confused::(

*edit*
nope... no firestarter..... im using hardy heron if that changes anything.....

---

### Post by Moop on 2008-04-17
Maybe this is what you wanted. [http://ubuntuforums.org/showthread.php?t=331161](http://ubuntuforums.org/showthread.php?t=331161)

I never needed to open a port in Ubuntu as long as I opened it in the routers firewall.

---

### Post by sisco311 on 2008-04-17
> **TeoBigusGeekus said:**
> Unless you have a firewall install (Firestarter for example)...

Firestarter is a GUI application for configuring the firewall.
The default firewall on Ubuntu is iptables 
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
[https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)

---

### Post by Tews on 2008-04-17
If you happen to be running 8.04 Hardy Heron it is quite simple with Uncomplicated FireWall.  Enter the following ..

```
sudo ufw enable
```

Once you have UFW enabled just specify which port you want opened..

```
sudo ufw allow xxxxx/tcp
```

replace xxxxx with the port you want opened.  If you need a udp port opened ..

```
sudo ufw allow xxxxx/udp
```

---

### Post by Fatal Equinox on 2008-04-17
> **Moop said:**
> Maybe this is what you wanted. [http://ubuntuforums.org/showthread.php?t=331161](http://ubuntuforums.org/showthread.php?t=331161)

I never needed to open a port in Ubuntu as long as I opened it in the routers firewall.

I think that worked.... azerus is not givening me that test error.... 

Thanks for the link,


*EDiT*

Thanks also tews.....

---

### Post by timcredible on 2008-04-17
were you just asking how to find out what ports aren't already used by the system?  if so, all ports used by processes are listed in /etc/services.

---

### Post by The Cog on 2008-04-17
If you need an incoming port, you have to configure your router to forward that port to your computer. If you have a modem so that there's no router and no address translation between you and the internet then this step isn't needed.

If you are not aware of having installed and started a firewall, then you don't have one running. If you do, either configure it to allow your chosen port number through or disable it for now.

Once you think you have an incoming port arranged, you can visit Shields Up [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2) and click Proceed. Then enter your chosen port number and click "User specified custom port probe". You should "fail" their test, which should report that the port is closed. This means that there is no firewall blocking it but no application is currently listening to hold the port open.

---

