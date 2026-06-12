---
title: "problem with wireless router &amp; Ubuntu"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by KevNice on 2008-02-06
My wireless router seems to randomly disconnect from the Internet. I guess its just an old router. But the problem is, when it disconnects, I am unable to re-connect without restarting Ubuntu. And something happens to the network manager that will not let me shut down properly (actually, when this happens, Terminal wont even open-- it starts to open, but then just doesnt). I get partway through shutdown and it says ```
Network Manager: activating kill signal
Deactivating device eth0
```

and it just kind of stops there. So I am forced to shut it down without logging off. Over time I am afraid it will damage my system. Is there anyway to prevent this from happening?

---

### Post by anewguy on 2008-02-06
I would be interested in an answer to this as well.  While not exactly what you get, I know that when my PC has a problem connecting to the router, I can reset the router, try to connect as a "new" connection, etc., but it always fails immediately.  A reboot of Ubuntu and everything is okay again.  I often get the same type of eth"x" problem at shutdown.

If it would help any, my wireless adaptor to my Pc (old PIII-500) connects to my PC via a USB port.

Thanks.:)

---

### Post by MariusSilverwolf on 2008-02-06
I used to have a similar problem, where the rest of my systems would stay online while my desktop would drop it's connection.  The only way I could reconnect would be to change the static IP I use on the system.  Too many times of this, and Network Manager would hang, and the rest of the kernel would stop responding.

I installed WICD ([http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)) and these problems went away.

I can't guarantee this will fix your issue, but it may help alleviate some things.

---

### Post by KevNice on 2008-02-07
Ive got Wicd install and running, and so far it does seem more stable. Ill let it go for a few more days and then post back here again

Thanks for that link!:)

---

### Post by KevNice on 2008-02-10
Ok, an update: 

When my Internet connection drops, I still cant reconnect without restarting Ubuntu. However, using Wicd, I now no longer have problems with shutting down and it lets me do it properly. So Wicd should work for you if you have this same problem

Thanks Marius!

---

### Post by KevNice on 2008-02-10
Actually I take that back. I think last time it crashed it was the modem itself. This time the router shut down and I wasnt able to shut it down properly again, just like with network manager. The problem persists.

what gives here?

---

