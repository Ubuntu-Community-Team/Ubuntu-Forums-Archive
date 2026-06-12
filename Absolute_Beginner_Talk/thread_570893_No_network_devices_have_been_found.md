---
title: "No network devices have been found"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by disappearedng on 2007-10-08
Hi everyone, I am using a Toshiba TE2100 with built in ethernet lan card. After installing ubuntu, I have been able to use internet fine until recently. 

1) I have direct internet access behind no routers/firewall 
2) I tried typing ifconfig -a | tee interfaces.txt and this is what came out

lo   line encap: local loopback
      inet addr: 127.0.0.1 Mask: 255.0.0.0
      UP loopback running MTU: 16436 Metric: 1
      Rx packets: 4 errors:0 dropped:0 overruns:0 frame:0
      Tx packets: 4 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:0
      Rx bytes:200 (200.0 b) Tx bytes: 200 (200.0.b)

I don't know whether this helps.

3) when i type route | routes.txt
it says routes.txt : command not found.

4) How can i activate 'add new hardware on ubuntu? I know my lan card did not die because i was JUST able to detect some networking device.

Any help pls?

---

### Post by philinux on 2007-10-08
ok what recently have you changed just before it stopped working?

---

### Post by disappearedng on 2007-10-08
SEE i don't recall what i did: 
I made some tweaks to firefox and that's about it 
I made some tweaks avaible here.

[http://cybernetnews.com/2006/06/07/tweak-ubuntu-to-maximize-performance/](http://cybernetnews.com/2006/06/07/tweak-ubuntu-to-maximize-performance/)

     Use InitNG as a replacement for standard Init.

    Speed up Firefox

    Custom compile a new kernel. You can also use this tutorial.

    Make sure DMA is enabled.

    Use Prelink to make applications start faster.

    Pick the kernel that’s right for your processor.

    Disable uneeded services from starting.

    Use Swiftfox, a faster Firefox for Intel and AMD processors.

    Tweak your ext3/reisers filesystem for enhanced performance.

    Disable IPV6 to make your internet faster. 

How can i restart network manager? It's still not working

---

### Post by philinux on 2007-10-08
So basically you've tweaked it so much it dont work now ?

Disable IPV6 to make your internet faster.  maybe this has something to do with it.

---

