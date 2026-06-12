---
title: "Is Ubuntu dependent on your Internet connection?"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by cdbillups on 2007-07-08
I've had Ubuntu for about 4 days.  I love it.  I just have one question.  I've been having some trouble with my ISP and I've lost Internet connectivity off and on for the past day.  I've noticed that when my connection is down, Ubuntu runs real slow.  Example: when my connection is up Terminal takes 2 seconds to open; when it's down Terminal took 20 seconds to open.  Does Ubuntu have to have an external network connection to operate properly?

---

### Post by oilchangeguy on 2007-07-08
the internet connection, or lack there of, should make no difference in your computers speed. remember, a computer is not only for accessing the internet, some people actually use them to get some work done (without an internet connection).

---

### Post by cdbillups on 2007-07-08
I wouldn't think so either.  That's why I'm asking.  It seems odd to me that whenever my Internet is down, the machine is slower.  I wasn't sure if it had some setting that was checking for updates to the program that I was trying to run or something like that.

---

### Post by Old Pink on 2007-07-08
How do you connect?

ISP trouble could mean you still have limited connectivity, meaning connect-disconnect-connect-disconnect loops could be affecting system resources and performance.

Have a look in system monitor, see what's hogging CPU/RAM? :)

---

### Post by sloggerkhan on 2007-07-08
It's possible you have activated some sort of service that is loading your comp until it times out.

---

### Post by eternalsword on 2007-07-08
It's possible when your internet goes down that the dhcp daemon or avahi's ip daemon or something similar keeps trying to get a connection, this is especially possible if you are using ethernet and not behind a router.  Best thing to do in that case is to disable the device used to connect eg ```
sudo ifdown eth0
```
in this case eth0 is the device.  Try disabling the device next time this happens.  You can always attempt a reconnect with ```
sudo ifup eth0
```

---

### Post by cdbillups on 2007-07-09
My ISP is a wireless Internet provider.  I plug into a WRT54G Linksys router that's running dd-wrt v.23.  The router plugs into their wireless radio.

I've checked the system resources and don't see anything that might be hogging the resources.

I'm not sure about the services.  I've checked under Administration - Services and took note of what was checked but didn't change any of the settings.

I'll try the command you listed to see if that helps out or not.  Thanks for the suggestions.

---

### Post by hyper_ch on 2007-07-09
well, IPv6 can slow down internet but that shouldn't have impact on how fast a terminal is opeend...

---

