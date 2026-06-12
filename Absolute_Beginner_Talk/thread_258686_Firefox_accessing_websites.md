---
title: "Firefox accessing websites"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by Marziepants on 2006-09-16
I just switched to ubunto 6.06 LTS and I can ping websites fine from the command prompt-equivalant program, but can't access them through Firefox. I'm using Windows on a different pc to post this. 

What should I do?

---

### Post by Najand on 2006-09-16
Are you behind a proxy server or something?

---

### Post by Marziepants on 2006-09-16
I'm behind a Netgear ADSL Modem Router DG632

---

### Post by Marziepants on 2006-09-16
Bleh I can't access the internet from other applications either, but I can still ping websites and get to other places on the network. I have yet to set anything up, so is there something i need to do to enable internet connections?

---

### Post by JayTee on 2006-09-16
Do you have a built in firewall in that router? If so you will need to open port 80 for HTTP. The other thing to check is if you have a firewall on your computer as well. Also, check your DNS setting on your computer running Ubuntu. It's obvious ICMP is working so something else at the next layer is blocking HTTP requests. Best of luck!

---

### Post by Marziepants on 2006-09-16
I don't have to open any ports to access the internet from my computers on XP, and on the router to add a custom firewall rule you have to choose between UDP and TCP? 

I haven't added any programs on the computer running ubuntu, and it's linked straight to the router and not through another computer, so I don't think there's a firewall there.

How would I go about checking DNS settings - what should they be like?

---

### Post by bakert on 2006-09-16
> **Marziepants said:**
> How would I go about checking DNS settings - what should they be like?

Have a look at the contents of /etc/resolv.conf to see what your DNS setup is.

If you can do stuff like

$ ping google.com

and get a response then that implies your machine CAN do name resolution, though.  Worth a look though - I've certainly had times where ping resolves but stuff like apt-get does not.  I can't remember why that was (sorry!)

I might be sending you off on a wild goose chase but I wonder if this might be related to ipv6.  My DLink router doesn't support it and that gave me some problems (Ubuntu uses ipv6 by default).  Try going into firefox and typing "about:config" (no quotes) into the address bar and pressing Enter.  Then type "ipv6" (again no quotes) into the search and change disabled to "true" by double clicking that line.  Can you then get to websites through firefox?

---

### Post by Marziepants on 2006-09-16
> **bakert said:**
>  Try going into firefox and typing "about:config" (no quotes) into the address bar and pressing Enter.  Then type "ipv6" (again no quotes) into the search and change disabled to "true" by double clicking that line.  Can you then get to websites through firefox?
Woot! That fixed Firefox! I'm not aching to get the IM working right now, so thanks for all your help :)

~My first post from an ubuntu machine

---

### Post by jordanmthomas on 2006-09-16
Personally, I don't like loading up ipv6 as it seems to slow down my network.  So, I make it never load up...
```

gksu gedit /etc/modprobe.d/blacklist
```
At the end, add this
```

#  Disable ipv6..
blacklist ipv6

```

When you reboot, all of your applications should work.

**edit**
You will also need to turn ipv6 back off in firefox if you do this
if it doesn't work, just undo the blacklisting and turn ipv6 back on in firefox.

---

### Post by spur on 2006-09-17
I disable ipv6 globaly and through forefox settings.All it does is slow things down to a crawl.

---

