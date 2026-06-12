---
title: "Internet says im connected, not working"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by kingfoot on 2007-06-14
I have just installed ubuntu (7.04) and all is fine, so first i need to get all those updates and drivers, well in order to get them i need to connect to the internet in ubuntu. problem is, when i connect my cat5 ethernet cable from my dsl modem, internet wont work. I ran "pppoeconf" input all the info, (and tried other various changes i could think of to make it work) and every time, it connects, says im connected to the internet, so i launch firefox and it sits there loading page (resolving host) and when i run something like "sudo apt-get update", the terminal sits there with a loading percentage and says connecting to such and such server, and then it says failed and tries another server. nothing ever happens. it says im connected, the modem's ethernet light blinks when i try to use the internet (like normal). I tried restarting with it connected, no luck. ive tried turning off the box (unplugged) for an hour and plug it back in. nothing works. obviously it is working now because im posting this (in windows vista)

---

### Post by wormser on 2007-06-14
This could be a DNS issue.  First try putting 64.233.167.99 in your browser.  If the page shows then it is a DNS issue.  Then add 4.2.2.2 and 4.2.2.1 as your DNS servers.

Other steps would be to see if you have an ip address.  Applications> Accessories> Terminal 

```
ifconfig
```

Also try pinging to an ip address and domain name.

```
ping 64.233.167.99
```

Let us know how it goes.

---

### Post by kingfoot on 2007-06-14
no luck. firefox gave me a "cannot connect to server" on that ip you told me to connect to, and adding the 2 dns servers didnt do anything. i tried ifconfig and it showed the eth port i have hooked up has an ip, pinging the server couldnt connect. i tried redoing the pppoeconf and it still didnt work.

---

### Post by kingfoot on 2007-06-14
any ideas?

---

### Post by BHelts on 2007-06-14
did you try unplugging your DSL modem for about a minute, then plugging it back in?

---

### Post by kingfoot on 2007-06-14
check my first post, i had it unplugged for about an hour, then i tried it again. i just did it again (off for about 2 minutes) and no luck still.

---

### Post by BHelts on 2007-06-14
whoops... sorry about that.  bad scan.

---

### Post by wormser on 2007-06-14
Post and search for your DSL providers name and model of modem.  Good Luck.

---

### Post by kingfoot on 2007-06-14
Provider: Centurytel
Box: Westell
where do i find the model of the box? on the sticker? which one is right there is a bunch of different things on it!

---

### Post by k1001001 on 2007-06-14
I had some issues with my DSL modem as well, and what fixed it was disabling IPv6. Maybe this will work for you as well. [Here]("http://ubuntuforums.org/showthread.php?t=304875") is a link to the thread I started when I was having these troubles. Follow the steps I took and see if it works for you then.

---

### Post by kingfoot on 2007-06-14
I ran through all those steps and it still wont work. though when i go to my router page (type in the ip of it) and i view status it says its not connected, that there are no open connections to it and it has no ip... yet ifconfig gives me a connected and an ip...

---

### Post by kingfoot on 2007-06-14
any more advice guys?

---

### Post by wormser on 2007-06-14
> **kingfoot said:**
> I ran through all those steps and it still wont work. though when i go to my router page (type in the ip of it) and i view status it says its not connected, that there are no open connections to it and it has no ip... yet ifconfig gives me a connected and an ip...

Are you able to log onto your router in Ubuntu?  If you can connect to the router then the problem is somewhere in your router but only happens when connecting from Ubuntu.

---

### Post by sachill on 2007-06-15
Hi.  Im having the same problem. Ive just updated from Ubuntu 5.04 to 7.04.  On the old edition I could connect to the internet. Now, after doing the same network configurations I did then, I canùt connect on 7.04  Please help.

---

### Post by Mazehero55 on 2007-06-15
Yep me too... only with cable though Maybe it's a bug in 7.04?

---

