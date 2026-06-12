---
title: "internet still slow....."
date: 2005-08-11
forum: Absolute Beginner Talk
---

### Post by Strongbad on 2005-08-11
Hello, it's me again. I can't seem to get my computer to connect to the internet at more than 28k. ](*,)  I have tryed the usual things like tweaking firefox and switching dial up programs, but nothing seems to be helping much. Is there some sort of speed setting that is holding my modem back? I have the port speed set at 115200, so that isn't the issue. Any ideas?

-Strongbad-

---

### Post by MrCheese on 2005-08-11
[QUOTE=Strongbad]Hello, it's me again. I can't seem to get my computer to connect to the internet at more than 28k. ](*,)  I have tryed the usual things like tweaking firefox and switching dial up programs, but nothing seems to be helping much. Is there some sort of speed setting that is holding my modem back? I have the port speed set at 115200, so that isn't the issue. Any ideas?

-Strongbad-[/QUOTE]

Your o/s won't influence the speed at which your modem talks over the internet.  Modems initiate a connection at the fastest rate they can, but subsequent problems such as line noise, echoes etc cause the speed to be downgraded until the error rates drop to an acceptable level.

It's likely that if you have been using Windows & have had fast connect speeds reported that you have been given the initial connect speed, not the "real world" speed that the modem is actually running at.

A fair speed comparison would be to time a file download in linux & Windows - there shouldn't be much difference as long as your line conditions are stable. You could try contacting your telco & ask them to increase the line gain, which usually helps if line quality is an issue.

Hope this helps,

Mr Cheese.

---

### Post by Strongbad on 2005-08-11
I've been using an online bandwidth test, and my windows machine tested at 40k. So I don't think it's the phone line.

-Strongbad-

---

### Post by Kapre on 2005-08-11
[QUOTE=Strongbad]Hello, it's me again. I can't seem to get my computer to connect to the internet at more than 28k. ](*,)  I have tryed the usual things like tweaking firefox and switching dial up programs, but nothing seems to be helping much. Is there some sort of speed setting that is holding my modem back? I have the port speed set at 115200, so that isn't the issue. Any ideas?

-Strongbad-[/QUOTE]

I'm also a nooby but had encountered the same problem when I was still using Fedora. Did you check your modem type (is this internal or external). Reason I'm asking is because we dont have all drivers for them.

Try scanning your modem type (manufacturer) so you can check if the correct driver is being used.

K

---

### Post by Strongbad on 2005-08-12
It's a 3com hardware controled internal modem. Other than that, I don't know much about it. How do I scan to see exatly what it is?

-Strongbad-

---

### Post by Kapre on 2005-08-12
[QUOTE=Strongbad]It's a 3com hardware controled internal modem. Other than that, I don't know much about it. How do I scan to see exatly what it is?

-Strongbad-[/QUOTE]

Try this link [https://wiki.ubuntu.com/forum/hardware](https://wiki.ubuntu.com/forum/hardware). You can also find some more info by using the search link and typing "scanmodem".

---

### Post by KingBahamut on 2005-08-12
StrongBad, your not StrongBad408 from BF2 are you?

---

### Post by mingus on 2005-08-13
[QUOTE=Strongbad]It's a 3com hardware controled internal modem. Other than that, I don't know much about it. How do I scan to see exatly what it is?

-Strongbad-[/QUOTE]

Are you positive it is a true hardware modem?  Internal modems are almost always soft modems.  You can download a scanning tool to tell you the chipset and required driver if a softmodem at:

[http://linmodems.technion.ac.il/](http://linmodems.technion.ac.il/)

This tool will scan the PCI (and ISA if it's there) bus and tell you what is there.

Also, if you can open the case and view the card, usually the chipset will be imprinted on it.  A good site to understand a particular modem is [www.modem-help.com](www.modem-help.com).

A true hardware modem operates independently of the OS and should not vary in speed.

BTW, some speed tests are wildly inaccurate.  Have you compared the results of a simple ping on an IP address (bypassing DNS)?

---

### Post by Strongbad on 2005-08-14
[QUOTE=KingBahamut]StrongBad, your not StrongBad408 from BF2 are you?[/QUOTE]

No, I'm just another homestarrunner.com nut  :) 

-Strongbad-

---

### Post by Strongbad on 2005-08-16
I think mabe the problem is that v90 isn't being used for some reason or another. Does anyone know anything about or had experience with that? I think it's using the ppp_generic module, is that the best one to use for a 3com us robotics hardware modem (by the way, I am sure it is a genuine hard modem)? Also, does anyone know why it is putting it on dev/ttyS14? Usually it's ttyS0 or ttyS1 isn't it?

-Strongbad-

---

### Post by Strongbad on 2005-08-18
Anyone there? :) 

-Strongbad-

---

### Post by mingus on 2005-08-18
It's been a hundred years since I played with modem configuration, and that was on W$ boxes, so take this just FWIW . . . your problem is not that uncommon, particularly with dial-up.  Taking a look at the forums at dslreports.com will give you a flavor, although now that is primarily dsl modem related not dial-up, as it was >5 yrs ago.  

You may have a problem in your network stack.  All internet devices have a TCP stack with parameters such as MTU which can affect performance.  Additionally there are parameters specific to a type of device; with dial-up modems that can be flow control, compression, and error correction.  Some of these are passed in the init strings, some are setup in the network or device configuration.  Usually the defaults work fine, but sometimes not so.  And since these parms are stored on the host system, the modem perf can differ from one host to another.

As far as the specifics, sorry, too long ago.  The following may be of help, also google the problem.  Once you determine which parameters are controlled where, you can try tweaking the modem.  

[http://www.tldp.org/HOWTO/Modem-HOWTO.html#toc2](http://www.tldp.org/HOWTO/Modem-HOWTO.html#toc2)
[http://www.aboutdebian.com/modems.htm](http://www.aboutdebian.com/modems.htm)

---

