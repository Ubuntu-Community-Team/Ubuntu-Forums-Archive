---
title: "Firewall Necessary?"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by AsYouWish on 2006-07-27
Hi

I've set up Ubuntu on an old mac running headless under my desk. Im just using it to bittorrent and bascially mess around a bit with Linux. It is set up with both SSH and VNC servers for remote administration, a samba share, and is behind a wireless router w/ built in firewall with WPA enabled. I only access it from machines behind the router.


Do I need to install and run firestarter? 

Thanks

---

### Post by T700 on 2006-07-27
I would say, "no."  Unless you are careless and forwarded ports from the router to open ports on your PC, there is virtually no hazard.  By default, all ports are shipped closed with Ubuntu, so the only ones that are open, are the ones you have manually set.

That said, there is no harm in using the built in IP Tables.  They are easily configured with Guard Dog or Firestarter.  Be sure to set rules to allow the remote apps you're using.

Paul

---

### Post by AsYouWish on 2006-07-27
Oh yeah i forgot to add... I have forwarded 4 ports through the router for use w/bittorent. So I guess thats a yes I do need it?

---

### Post by T700 on 2006-07-27
> **AsYouWish said:**
> Oh yeah i forgot to add... I have forwarded 4 ports through the router for use w/bittorent. So I guess thats a yes I do need it?

Not really, because to use bittorent, you'd have to open the port in the firewall, so I don't think you'd gain anything, anyway.  Hopefully someone will come by to provide a more authoritative answer, but I'm still not convinced that a firewall will add anything to your security.

Paul

---

### Post by steve.horsley on 2006-07-27
I'm with T700 on this one. 

If you ever let SSH in remotely then you will want a firewall to restrict who can connect or a certificates only configuration - there are lots of SSH password guessing bots out there.

---

### Post by AsYouWish on 2006-07-28
That sounds great - no firewall for me! (better than my XP laptop w/Zonealarm, A/V, Spybot,AdAware,SpywareBlaster). Im trying to keep the number of things running to a minimum anyway. 

Thanks alot.

---

### Post by OU812 on 2006-07-28
Hello, is firestarter configured to launch during the boot process or do you have to turn it on manually? (I'm doing some maintainence in win so I can't check for awhile.)Thanks.

john

---

### Post by T700 on 2006-07-28
Firestarter is the configuration tool for the built in firewall in Linux.  It does not have to be started nor running at all times.

Paul

---

