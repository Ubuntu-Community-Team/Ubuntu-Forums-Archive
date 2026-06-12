---
title: "[SOLVED] Home Security systems"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by Ex-windows on 2008-01-08
Hello all, 
I'm not sure if this is the right spot for this but here goes. Are there Any home security programs available for linux? Specifically, I want to use my web cams to monitor various parts of the property, and be able to view the cams on the main montior or all networked monitors.I found one here 
[http://misterhouse.sourceforge.net/](http://misterhouse.sourceforge.net/)
But this seems way beyond my skills at this time. Is there anything a lil simpler .
TIA

---

### Post by georider on 2008-01-09
You can have a look at Motion here: [http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome](http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome)

It's fairly easy to set up and quite fun to play with. AND it's in your repositories

Just
```
 sudo apt-get install motion 
```
Edit the /etc/motion/motion.conf and fire it up. If your webcams are supported and set up, there should be no trouble!

Another possibility is Zoneminder: [http://www.zoneminder.com](http://www.zoneminder.com)

It's also in the repositories
```
 sudo apt-get install zoneminder 
```
Zoneminder takes a bit more to set up as it requires a web server.

IMHO, motion is a quick and easy way to monitor webcams. If your webcam is up and working, you can be receiving emails of your 'suspects' in minutes.

Have fun!

-g

---

### Post by Ex-windows on 2008-01-09
Thanks loads for the info, :)   I was beginning to lose hope lol. This program sounds like just the ticket. Thanks again

---

