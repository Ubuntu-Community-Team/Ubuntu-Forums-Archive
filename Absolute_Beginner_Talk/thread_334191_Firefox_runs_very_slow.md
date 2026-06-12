---
title: "Firefox runs very slow"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by brandoncolorado on 2007-01-08
Hi all,

I am running a gateway mx3414 with Turion x64 processor.  The computer runs great in Windows, and even most of Ubuntu.  When I run firefox, I get a lot of lag.  It is not lag in the browser window (the actual webpage), it is the program.   Things like switching tabs or scrolling down show an irritating lag.  Is there something I could do to fix a problem like this?  I am using 2.0.0.1

---

### Post by justifier on 2007-01-08
hrm, sounds strange, have you tryed re-installing firefox ? does this fix it? have you tried different browsers? does it happen with them?

---

### Post by brandoncolorado on 2007-01-08
Hi Justifier,

Thanks for the response.  I tried uninstalling and reinstalling firefox from synaptics and that didn't fix the problem.  I tried Opera (downloaded the package from their website) and I do not have the same problem.

---

### Post by c-ron on 2007-01-08
You may wish to try building Firefox from source, or try using a build of firefox which has already been built with optimizations for your processor's architecture, such as Swiftfox.
You can find the AMD 64 build of Swiftfox at [http://getswiftfox.com/rel-athlon64.htm](http://getswiftfox.com/rel-athlon64.htm) 

Note: You can use firefox and swiftfox side-by-side and get them to share plugins, and add-ons, themes, etc..

Hope this helps! ;)

---

### Post by brandoncolorado on 2007-01-08
Thanks, I'll try out SwitftFox.  Would the athlon version work on my turion system?

---

### Post by kent41 on 2007-01-08
> **brandoncolorado said:**
> Hi all,

I am running a gateway mx3414 with Turion x64 processor.  The computer runs great in Windows, and even most of Ubuntu.  When I run firefox, I get a lot of lag.  It is not lag in the browser window (the actual webpage), it is the program.   Things like switching tabs or scrolling down show an irritating lag.  Is there something I could do to fix a problem like this?  I am using 2.0.0.1

I wonder if IPV6 is giving you a problem in Ubuntu it is enabled by default and it seems some must disable IPV6 for Firefox to work properly.
 
I find that Firefox  brings web pages up 4 to five time faster than IE.

---

### Post by c-ron on 2007-01-08
The version of swiftfox listed on [http://getswiftfox.com/rel-athlon64.htm](http://getswiftfox.com/rel-athlon64.htm) *should* work with your Turion, however, I use an intel chip, so I can't be certain.

---

### Post by philip360 on 2007-01-08
> **kent41 said:**
> I wonder if IPV6 is giving you a problem in Ubuntu it is enabled by default and it seems some must disable IPV6 for Firefox to work properly.
 
I find that Firefox  brings web pages up 4 to five time faster than IE.

Kent, could you clarify what you mean by your reply? I have the same problem but don't understand how to check or modify in regards to your suggestion. Thanks, Philip

---

### Post by geo_bio on 2007-01-09
Is it ONLY firefox? or is it anything with processing or graphics?

I believe you need a "kernel" if you want more support for your processor, and a graphics driver for Linux.

For the kernel, look here. It may not be necessary though:
[http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)

---

### Post by scrooge_74 on 2007-01-09
> **kent41 said:**
> I wonder if IPV6 is giving you a problem in Ubuntu it is enabled by default and it seems some must disable IPV6 for Firefox to work properly.
 
I find that Firefox  brings web pages up 4 to five time faster than IE.

This is the way to disable ipv6

[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)

---

### Post by MkfIbK7a on 2007-01-09
well firefox IS faster than IE but is slower than everything else (epiphany, opera, dillo)
i myself would recommed downloading opera...

---

### Post by IusedTObeSOMEONEelse on 2007-01-09
So true, firefox so slow and lags. I found swiftfox to be quite responsive. Just my thoughts. :D  Sally

---

### Post by deadgobby on 2007-01-09
What ever you do. DO NOT REMOVE FIREFOX. It will break your system if you uninstall it and reboot. 
 If you want to speed up FF please try this.
[https://wiki.ubuntu.com/FirefoxTipsAndTricks?highlight=%28firefox%29#head-922e077aa1ab92626e25e4dda9615a14aa91109f](https://wiki.ubuntu.com/FirefoxTipsAndTricks?highlight=%28firefox%29#head-922e077aa1ab92626e25e4dda9615a14aa91109f)

Gobby

---

### Post by maniacmusician on 2007-01-09
the problem is not IPV6, it's the horrible XUL design of firefox. It pretty much murders my computer as well when I have even 9 or so tabs open (and I usually do).

IPV6 could be to blame if it were his web pages that were loading slowly, but OP clearly said that it was the program lagging, not his connection or the loading of pages.

---

### Post by kent41 on 2007-01-09
> **philip360 said:**
> Kent, could you clarify what you mean by your reply? I have the same problem but don't understand how to check or modify in regards to your suggestion. Thanks, Philip


Bring up your browser and at the address line enter ABOUT:CONFIG and push the ENTER button and then below the address line you will see a FILTER line. At the filter line enter IPV6 this will bring up the following line.

```
Network.dns.disableIPV6    and the VALUE will be FALSE 
```

Double click on the FALSE VALUE and that will change the VALUE to TRUE

I hope this helps.

---

### Post by philip360 on 2007-01-09
> **kent41 said:**
> Bring up your browser and at the address line enter ABOUT:CONFIG and push the ENTER button and then below the address line you will see a FILTER line. At the filter line enter IPV6 this will bring up the following line.

```
Network.dns.disableIPV6    and the VALUE will be FALSE 
```

Double click on the FALSE VALUE and that will change the VALUE to TRUE

I hope this helps.

Thanks Kent and DeadGobby! Both your suggestions worked great, I now don't have time to make a cappuccino while a page is loading! Philip

---

### Post by vladverzeni on 2007-01-09
> **kent41 said:**
> Bring up your browser and at the address line enter ABOUT:CONFIG and push the ENTER button and then below the address line you will see a FILTER line. At the filter line enter IPV6 this will bring up the following line.

```
Network.dns.disableIPV6    and the VALUE will be FALSE 
```

Double click on the FALSE VALUE and that will change the VALUE to TRUE

I hope this helps.



I´m having the same problem. (firefox is reallly laggy in ubuntu)  I changed this value and I did not notice a change for better or worse...

I have a newer computer with a Pentium D chip.   The first thing I thought was that maybe ubuntu had latched onto my onboard video card rather than the Radeon one I put in later.

---

### Post by philip360 on 2007-01-09
> **vladverzeni said:**
> I´m having the same problem. (firefox is reallly laggy in ubuntu)  I changed this value and I did not notice a change for better or worse...

I have a newer computer with a Pentium D chip.   The first thing I thought was that maybe ubuntu had latched onto my onboard video card rather than the Radeon one I put in later.

Hi Vlad, I combined the IPv6 step with others. Look up this thread for the response from deadgobby. He gave the link:  [https://wiki.ubuntu.com/FirefoxTipsA...615a14aa91109f](https://wiki.ubuntu.com/FirefoxTipsA...615a14aa91109f)

I did the config from the link also. The link gives info for firefox 1.5 and I am running 2.0. They worked, but there were 2 that were not listed in the config list, so I did not worry about them. Hope that helps, Philip

---

### Post by varnerin on 2007-01-09
I had the same issue.  I fixed by:

network.dns.disableIPv6-> Set to True

8)

---

### Post by brandoncolorado on 2007-01-13
Alright, I installed Opera and it was running smoothly, but now I am able to replicate the same problem in Opera.  To be more specific, here is the page that absolutely kills Opera.

[http://victor-serrano.com/index.php?blog=6&title=gateway_mx3410_drivers&more=1&c=1&tb=1&pb=1](http://victor-serrano.com/index.php?blog=6&title=gateway_mx3410_drivers&more=1&c=1&tb=1&pb=1)

I almost can't scroll.  Takes me almost a minute to scroll to the bottom, and I can't move.  Other pages have had similar difficulty.

---

### Post by scrooge_74 on 2007-01-13
I using no proble seeing that page, you may have other issues besides firefox

---

### Post by brandoncolorado on 2007-01-28
> **scrooge_74 said:**
> I using no proble seeing that page, you may have other issues besides firefox

I have disabled IPv6 and am having the SAME problem.  Another great example of a page that kills me is the second page of the Digg article submission.  I literally can't move.  I don't know what it is about the page, but I can't see any flash etc.

What else could I try?

---

### Post by brandoncolorado on 2007-01-28
Also, I am not having the same problem in Opera.

---

### Post by scrooge_74 on 2007-01-29
Ran out of ideas, maybe uninstall firefox and reinstall? Maybe that will clear up the problem, right now there is an update to firefox

---

