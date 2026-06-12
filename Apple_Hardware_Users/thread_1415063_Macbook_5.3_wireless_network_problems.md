---
title: "Macbook 5.3 wireless network problems"
date: 2010-02-24
forum: Apple Hardware Users
---

### Post by langmore on 2010-02-24
Recently a new problem has shown up.  My network connection periodically dies.  For example, sometimes I am disconnected from my home wireless network.  I can then reconnect, but sometimes have to wait a minute.  Also, when I am watching youtube the video will stop downloading.  Also, when trying to access a web site, sometimes there will be a long wait.  (This latter issue has actually been there for some time, but recently got worse).  When I reboot and use mac OSX there is no issue.

My specs:
Computer:  MacBook Pro 5.3
Network: 802.11 draft n.  
Router:  DLink DIR 635 (D link, D-link)
OS:  Karmic,  64 bit
Driver packages installed:  bcmwl-modaliases,  bcmwl-kernel-source  
Drivers in use:  Broadcom STA wireless driver

---

### Post by linuxopjemac on 2010-02-24
I might be wrong, but it seems that the driver on the [broadcom site]("http://www.broadcom.com/support/802.11/linux_sta.php") is newer than [the one you are using]("http://packages.ubuntu.com/da/karmic/bcmwl-kernel-source") (around a year difference).

You might want to try to uninstall bcmwl-kernel-source and to install the newer one from the Broadcom site.

---

### Post by langmore on 2010-02-27
I installed the new Broadcom driver.  The same problem still exists.  Any other ideas?

---

### Post by linuxopjemac on 2010-02-28
You probably use networkmanager. My experience is that wicd is better than networkmanager. You might want to switch to that:
```

sudo apt-get install wicd
```

reboot and try again

---

### Post by langmore on 2010-03-01
That didn't help.  I'm going to try a new router.  I believe that the current trouble existed all along, but I was so "in love" with my new computer that I didn't notice it.

---

### Post by linuxopjemac on 2010-03-02
I hope that helps. I am not so sure. Did you try OSX ?

---

### Post by langmore on 2010-03-06
While using OSX everything is fine.  I haven't been able to test the computer near a different router.  I will soon.

---

### Post by langmore on 2010-03-23
I tried things with two new routers, and things work fine.  So the Dlink router seems to be the issue.

---

### Post by linuxopjemac on 2010-03-23
great! Can you edit your post as "SOLVED" pls?

---

### Post by GermanGiant on 2010-03-23
Glad your problem was so simple. I had a mac wireless problem recently and somehow the frame got bent up just enough so that the wireless antenna no longer connected to the motherboard. And it couldn't be replaced without hundreds in expenses!

---

### Post by langmore on 2010-04-06
How do I edit this post as SOLVED?  I don't really know what that means, although I guess it means I change the title of the post.

Thanks

---

### Post by linuxopjemac on 2010-04-06
You see in red, thread tools, I think you can set it there. Or one of the other two red ones...

---

### Post by FK888 on 2010-04-07
I hope it works

---

### Post by langmore on 2010-05-05
It looks like it wasn't in fact solved.  While there are less problems with the new router, some new ones still persist.  

1.  My connection occasionally is cut out, and reconnects about 30 seconds later  (this doesn't happen while using mac os X)
2.  Sometimes when I restart, a network connection is never established, and wicd doesn't find any available networks.

I'm gonna try reverting back to the default network manager and see what happens.  We also have access to a third router, so I can try that.  For problem #1 it is possible that my router or cable model occasionally loses its signal, and that mac os X is just better at re-connecting.

---

### Post by vegham on 2010-05-08
I have the exact same machine and problem, but I´m using DLINK-655 router.

Ubuntu is able to find nearby routers, but are unable to connect. Well, it connect some times, randomly, but usually I´m without net :(

Where should I look for a solution?

---

### Post by linuxopjemac on 2010-05-08
weird. With the STA driver it is supposed to work. What happens if you change the encryption to say WEP or open ?

---

### Post by vegham on 2010-05-10
Open works, WEP works and WPA works some times. Managed to get WPA to work this time.

---

### Post by langmore on 2010-05-16
After a week of fiddling around, problem #2 is specific to kernel 17.  Kernel 21 only shows issue #1.  I was using 17 because sound doesn't work with 21.  I've heard that upgrading (I have Karmic) helps the sound issue...

---

### Post by breimer273 on 2010-05-16
> **langmore said:**
> It looks like it wasn't in fact solved.  While there are less problems with the new router, some new ones still persist.  

1.  My connection occasionally is cut out, and reconnects about 30 seconds later  (this doesn't happen while using mac os X)
2.  Sometimes when I restart, a network connection is never established, and wicd doesn't find any available networks.

I'm gonna try reverting back to the default network manager and see what happens.  We also have access to a third router, so I can try that.  For problem #1 it is possible that my router or cable model occasionally loses its signal, and that mac os X is just better at re-connecting.

I am having problem number 1 as well. I am using a Netgear 802.11n router with the macbook pro 5,5. When I am at school I am using a Netgear router but the encryption is only WEP not WPA2 like I use at home. Could this be the issue? If so I guess I can down grade and then use some other protections (I don't really NEED WPA2 ecryption). I am using lucid with the STA wireless driver. In trying to write this post my internet connection disconnected twice. Tomorrow I will try downgrading to WEP security but I don't think that is a permanent solution for other end users. Also it is loading REALLLY slow and no other computers on the network have this problem. I'll post the results of changing to WEP tomorrow night probably but if anyone has any other ideas that would be great.

---

### Post by linuxopjemac on 2010-05-16
Maybe I said it before but my experience with wicd is much better than with network-manager.

---

### Post by breimer273 on 2010-05-18
Alright so testing it with WEP security worked fine. It seems that there is a problem staying connected to WPA2 encryption. I will try wicd and let you know how that goes.

---

### Post by breimer273 on 2010-05-18
Well wicd was a no go. It didn't even find a network to connect to at all...

---

### Post by langmore on 2011-03-17
I never got things working consistently, so I upgraded to 10.04 Lynx.  "Out of the box" things didn't work, so I tried the solution suggested at:  [http://ubuntuforums.org/showthread.php?t=1705143](http://ubuntuforums.org/showthread.php?t=1705143)

Now it takes a minute to connect:  When I start the computer, wicd searches for networks for a minute, then asks for my password (it is stored so I don't know why it asks...) then when I tell them to use the password I am connected.  If I try to connect before then I get an "invalid password" error.  Anyone know what is going on?

---

### Post by langmore on 2011-04-04
I was being stupid.  I had WICD and network manager both installed.  Once uninstalling network manager, things work perfectly.

---

