---
title: "[SOLVED] Firestarter fails to start firewall"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by speirint on 2007-11-12
Every time I tried to run firestarter I got this:
> 

Failed to start firewall

The device sit0 is not ready

Please check your network device settings and make sure your internet connection is active.


I also saw that gutsy couldn't start Firestarter when I was updating but that it said it was a non fatal error yesterday... What does the stuff above mean, and what does it mean by saying network device settings need to be checked? What should I be doing since my internet connection certainly works every time I try running firestarter.

---

### Post by por100pre1 on 2007-11-12
That issue occurs if the network connection is not ready when Firestarter starts.

---

### Post by speirint on 2007-11-13
Connection is not ready when firestarter starts? My concern is that I already do have connection (I am using internet, I've been able to get updates and upgrades, etc.) and firestarter continues to say the same thing regardless.

---

### Post by Caffeine_Junky on 2007-11-13
I am not sure exactly what the problem is, ..so I thought I would make a suggestion:

1). Totally remove firestarter via 'Synaptic Package Manager' and reinstall
1a). run the setup wizard

2). Have a look at this:
[URL="http://ubuntuforums.org/showthread.php?t=542756&highlight=howto+firestarter"]
How-To: Firestarter on startup (better & safer way)[/URL]

---

### Post by speirint on 2007-11-13
I believe I figured it out, I took your advice and uninstalled it completely then put it back in.  Upon the start up screen, it gave me a choice between sit0 and eth0. Apparently firestarter was using something that I don't really use for internet* (I say this with an asterix because I honestly am not very versed in how networks, ethernet, and internet works) which was listed as sit0 IPc6 tunnel.  I also have eth0, which I assumed actually works for internet (and it is now listed as eth0 internet).

Thanks caffiene junky, I'm learning already.

---

