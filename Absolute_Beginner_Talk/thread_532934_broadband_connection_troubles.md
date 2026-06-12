---
title: "broadband connection troubles"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by Riffer on 2007-08-23
]Hiyas

I seem to have a weird connection problem.  We have a small home network, with xp on one machine and Ubuntu on the other.  Both go through a wireless router (Linksys wrt54gs), the Ubuntu machine is wired directly into the router, while the XP machine is wireless.  Under normal circumstance both are getting reasonable connection speeds.

The problem comes when the Ubuntu machine is used to get torrents or file transfers using irc or anything else similar.  Connection speeds with these type transfers are slow (best I ever got was 40 kbs) and it seems to throttle the bandwidth.  The funny thing is if I download updates and apps from the repositories the connection speed is great (up to 300 kbs) and it doesn't throttle the bandwidth.

I have searched through the forums and tried and tweaked many things, and yes the router has been port forward to allow these apps to get through the router.  Right now I have it running the best it has been, by re enabling ip6 and using firestarter to open some ports,  but still throttles our bandwidth.  

This was never the issue when the ubuntu machine was running win2000.  I am also unclear to whether Ubuntu is firewalled by default or not.  Also it seems that the router is not seeing the ubuntu machine.  Any thoughts?

---

### Post by Inxsible on 2007-08-23
> **Riffer said:**
> ]Hiyas

I seem to have a weird connection problem.  We have a small home network, with xp on one machine and Ubuntu on the other.  Both go through a wireless router (Linksys wrt54gs), the Ubuntu machine is wired directly into the router, while the XP machine is wireless.  Under normal circumstance both are getting reasonable connection speeds.

The problem comes when the Ubuntu machine is used to get torrents or file transfers using irc or anything else similar.  Connection speeds with these type transfers are slow (best I ever got was 40 kbs) and it seems to throttle the bandwidth.  The funny thing is if I download updates and apps from the repositories the connection speed is great (up to 300 kbs) and it doesn't throttle the bandwidth.

I have searched through the forums and tried and tweaked many things, and yes the router has been port forward to allow these apps to get through the router.  Right now I have it running the best it has been, by re enabling ip6 and using firestarter to open some ports,  but still throttles our bandwidth.  

This was never the issue when the ubuntu machine was running win2000.  I am also unclear to whether Ubuntu is firewalled by default or not.  Also it seems that the router is not seeing the ubuntu machine.  Any thoughts?

Most times, the ISP will block or throttle the bandwidth, if they identify you as a heavy user. Most ISPs also throttle known ports for P2P software like torrents and emule etc. Your option would be to use non-standard ports in torrent applications.

You could also contact your ISP and find out about their network blocking schemes and rules.

As to why this wasn't happening on your Win2000 earlier, maybe your ISP hadn't recognized you as a heavy user or you were using a non standard port in the apps there.

Ubuntu does come with a firewall by default. It is also switched on but I think you have to tweak it a bit to suit your system.

---

### Post by kornface13 on 2007-08-23
What speeds do you get if you start torrenting on your windows box?

I just recently switched to Ubuntu, and when I started using Azureus my speeds sucked.  It pissed me off, so I switched to Deluge, and i'm plenty happy with it until utorrent releases a real Linux version.  I hate wine (from my minimal experience with it), so I'm doing everything I can to stick to "real" linux stuff.

Try out deluge and see what you think.  Also try turning off your firewall for a little while.  After you are 100 percent sure all your configs are correct, start up your torrents, and let them sit for a little bit so they can accept some connections.  

Is your Linksys firmware up to date?  Linksys boxes are sometimes bad for holding connections for WAY too long and it results it everything getting clogged up.  

Who is your ISP?  Maybe we can rule the whole throttling thing out.....


What firewall does Ubuntu come with?  How do I configure it?  I didn't think it had a firewall because it wasn't really needed.....

---

### Post by Inxsible on 2007-08-23
> **kornface13 said:**
> What firewall does Ubuntu come with?  How do I configure it?  I didn't think it had a firewall because it wasn't really needed.....

Ubuntu comes with a default firewall called iptables. You can tweak this firewall using a GUI app like FireStarter or GuardDog

```
sudo aptitude install firestarter
```or ```
sudo aptitude install guarddog
```

---

### Post by Riffer on 2007-08-23
On the windows side depending on seeding etc I get up to 100 kbs.  But the main trouble I am having is that the whole network bogs down whenever I download a torrent no matter what the connection speed is.

Also while I have an internet connection and can see the other computer on my network, the router doesn't see the Ubuntu machine.  The router is encrypted and I wonder if thats the problem, that I haven't set the encrption key for ubuntu.  And thats something I can't figure out how to do.

Right now I've disabled the firewall using Guarddog and am seeing how that works.

---

