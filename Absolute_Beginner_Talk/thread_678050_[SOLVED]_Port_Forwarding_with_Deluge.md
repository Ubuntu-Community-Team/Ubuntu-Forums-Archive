---
title: "[SOLVED] Port Forwarding with Deluge"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by newbeeman on 2008-01-25
I could do with some help with Port Forwarding and using Deluge.

I need to use a specific port, my ISP throttles the 'normal' ports used by Torrents, leading to slow speeds.

 I know how to Port forward, used it before in Win, but moving to UB and Deluge I get a port closed signal when testing active port.

I did try using Utottent under wine, but that failed the test as well.

Would welcome a discussion.

---

### Post by rhc on 2008-01-25
If you opened port no. 1200 for ex.
Go Edit Preferences>Network
Make port from=1200 to=1200
Then restart deluge and test it. Preferences>Network again.

---

### Post by newbeeman on 2008-01-25
> **rhc said:**
> If you opened port no. 1200 for ex.
Go Edit Preferences>Network
Make port from=1200 to=1200
Then restart deluge and test it. Preferences>Network again.

Could you please elaborate. 
I tried System/preferences all I can find is Network Proxy and there is nothing in there about Ports.

---

### Post by rhc on 2008-01-25
Open Deluge and the preferences of the program.
Not from system.

---

### Post by newbeeman on 2008-01-25
Our posts crossed. I realised my error. Tried again, but it made no difference in Deluge.

---

### Post by mikewhatever on 2008-01-25
You don't need to forward ports unless you are behind a router. Use random ports in Deluge, so that your ISP may have difficulties tracking them, and also, try using forced encryption. All these settings are in Deluge, Preferences, Network.

---

### Post by rhc on 2008-01-25
Are you sure that you opened the ports correctly?
Open a new port both the same number for UDP and TCP.
Write it "from: to:". Close the program.
When you open Deluge preferences>network again,
there should be a "TCP active port:no" there.
Make sure it s the same as you write to "from: to:" section.
Then test port.

---

### Post by newbeeman on 2008-01-25
> **rhc said:**
> Are you sure that you opened the ports correctly?
Open a new port both the same number for UDP and TCP.
Write it "from: to:". Close the program.
When you open Deluge preferences>network again,
there should be a "TCP active port:no" there.
Make sure it s the same as you write to "from: to:" section.
Then test port.

Sorry guys, I have done all that. I am behind a router, have used Port Forward and followed all the instructions, including the ones from 'mikewhatever'
When I test the 'Active port' in Deluge I still get port closed, and I know from experience I'll get slow speeds.

---

### Post by mikewhatever on 2008-01-25
> **newbeeman said:**
> Sorry guys, I have done all that. I am behind a router, have used Port Forward and followed all the instructions, including the ones from 'mikewhatever'
When I test the 'Active port' in Deluge I still get port closed, and I know from experience I'll get slow speeds.

If you are behind a router (should have mentioned it before), do not use port randomization, because forwarding would not work that way. Check out this site [http://portforward.com/](http://portforward.com/).

---

### Post by newbeeman on 2008-01-25
> **mikewhatever said:**
> If you are behind a router (should have mentioned it before), do not use port randomization, because forwarding would not work that way. Check out this site [http://portforward.com/](http://portforward.com/).

Sorry, this is no help. Am moving this thread to the Deluge web site.
Hope I haven't offended anyone.

---

### Post by chronniff on 2008-04-01
I have had the same problem with deluge not recognizing the port to be open...but as I have not really noticed any speed deficiency I have left it alone assuming that it is just one of the many bugs in deluge....( I too am behind a router and have configured the router to forward my designated port)

---

### Post by philinux on 2008-04-01
I use deluge behind a router and just use random ports. Never had any problems. Two different routers too with default configuration.

---

### Post by chalewa on 2008-04-07
yea i have the same problem with deluge. it is for sure not recognizing the right port, even though i have it specified in the preferences area. the port is open in my router configuration. 


what is also really weird is when i hit the 'test port' button in deluge, it tries to test the wrong port (a random one that is not specified in deluge). I have to manually change it to the port i do have specified, even though i know i do have it open.

---

