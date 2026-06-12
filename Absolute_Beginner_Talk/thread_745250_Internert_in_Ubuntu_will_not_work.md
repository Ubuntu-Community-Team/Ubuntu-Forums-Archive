---
title: "Internert in Ubuntu will not work"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by jojo2 on 2008-04-04
I recently decided to install ubuntu on a secondary hard drive over my previous installation of PClinuxOS, which was purely being used as a recovery OS. However I soon discovered that my internet connection didn't seem to work with it,I tried using other didstro's with similar results. Also, when I attempt a full install it hangs on the "Scanning the mirror" step. Does anyone have any idea as to why this is happening?

---

### Post by mtbeedee on 2008-04-04
It sounds like there isn't support for your network card.  Especially since you say it doesnt work in other distros either.  What kind of card do you have?  Try googling for that card and linux to see which module you need.

---

### Post by jojo2 on 2008-04-04
Im running an intel pro/1000 MT.
However Ubuntu can see the connection, and PClinuxOS could access the internet, which leads me to believe that its perhaps a configuration problem.

---

### Post by mtbeedee on 2008-04-04
How do you get addresses?  is the machine getting a proper IP address?  And are the routes correct?

---

### Post by jojo2 on 2008-04-04
I connect through a routerand the Ip appears to be set up fine.

---

### Post by zvacet on 2008-04-04
Try [http://ubuntuforums.org/showthread.php?t=704585&highlight=pppoe]this #6]()

---

### Post by yaztromo on 2008-04-04
From the livecd:

What is the output of lspci? Can you see your network controller in there?

What is the IP of your router/gateway?

Is DHCP turned on on the router?

Can other machines access the net okay on your LAN?

What is the output of ifconfig?

What is the output of cat /etc/network/interfaces?

What is the output of ping 192.168.0.1?

What is the output of ping [www.yahoo.co.uk?](www.yahoo.co.uk?)

That should give you some clue as to what is going on. If not post the results.

---

