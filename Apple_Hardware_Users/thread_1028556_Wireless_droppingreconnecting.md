---
title: "Wireless dropping/reconnecting"
date: 2009-01-02
forum: Apple Hardware Users
---

### Post by Craigular.B on 2009-01-02
Hello again!

I haven't needed to use the wireless in Ubuntu 8.10 until just recently because I had wired ethernet in my dorm. But when I came home for break, I found that when I use the wifi card, every so often it drops the connection and automatically reconnects. I'm using the Broadcom STA driver in the "Hardware Drivers" menu. My laptop is a Macbook Pro 4,1 Penryn. Under OSX the system profiler gives a firmware version of BCM43xx.

Any ideas?
Thanks!
-Craig

---

### Post by stream303 on 2009-01-05
If you don't need absolute speed, and it may be limited by the speed of the dsl / cable service anyway, maybe telling the card to drop it's own speed might help.  It helped when I had some random disconnects since my dsl is less than 1mb anyway, so the "G" speeds of 54mb aren't really needed.

You can do this from the cli - let's try 5.5M for wlan0 :  (substitute whatever your system uses for wifi...)

```
sudo iwconfig wlan0 5.5M fixed
```

You could also do that very early on by putting that line in your **/etc/rc.local** *before* the last exit 0 line without sudo.
```

# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

iwconfig wlan0 rate 5.5M fixed

exit 0

```

Typical values to knock down to are 54M, 24M, 11M, 5.5M, 2M and 1M

---

### Post by hyperboloid on 2009-01-06
> **Craigular.B said:**
> Hello again!
I found that when I use the wifi card, every so often it drops the connection and automatically reconnects. I'm using the Broadcom STA driver in the "Hardware Drivers" menu. My laptop is a Macbook Pro 4,1 Penryn. Under OSX the system profiler gives a firmware version of BCM43xx.


I also experienced the same problem. so I installed WICD [http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/") following the Ubuntu instructions on that site, and I have not yet dropped a wireless connection after a couple of weeks.

---

### Post by Dustin2128 on 2009-01-06
There's a package of wireless drivers in the repos, mabye you need a new one

---

### Post by Craigular.B on 2009-01-07
Thanks for the responses guys....When I go somewhere with wireless (the wifi in my dorm room isn't reliable enough to do any sort of conclusive testing with dropping connections) I'll be trying these in order to see how it goes. I'll post back and let you know!

-Craig

---

