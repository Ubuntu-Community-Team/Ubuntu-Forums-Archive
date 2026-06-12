---
title: "Wireless Internet Problem"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by spamzilla on 2007-03-07
I can connect to my wireless internet when I go to

> about:config > set the ipv6 value setting to true

gaim won't connect to the net. When I disable this option nothing will connect to the net. For the ipv4 setting, it's value is set to ".doubleclick.net." Is this meant to be there, and not, what should it be?

If this isn't the problem, then I am clueless as to what is the problem as everything worked fine yesterday!

Cheers

Matt

---

### Post by dotman on 2007-03-07
What ip values are you talking about? network.dns.disableIPv6 and network.dns.ipv4OnlyDomains?

---

### Post by spamzilla on 2007-03-09
Yeah.

My internet started randomly working again, but now won't even connect to my router...i didn't change any settings when it stopped working. Thankfully enough, wireless still works on the older Edgy kernel (2.6.15.23) so I'm using that kernel to access the net. The newer kernel where my internet doesn't work is 2.6.17.11.

Does anyone have any ideas as to what is wrong?

Cheers

---

### Post by spamzilla on 2007-03-09
bump

---

### Post by spamzilla on 2007-03-10
This is still a problem :(

> **spamzilla said:**
> Yeah.

My internet started randomly working again, but now won't even connect to my router...i didn't change any settings when it stopped working. Thankfully enough, wireless still works on the older Edgy kernel (2.6.15.23) so I'm using that kernel to access the net. The newer kernel where my internet doesn't work is 2.6.17.11.

Does anyone have any ideas as to what is wrong?

Cheers

---

### Post by dotman on 2007-03-12
Unless you are using ipv6 there is no reason that 'network.dns.disableIPv6' should be false (as in not disabled). Why that effects gaim, I don't know. If you are not using ipv6 you may want to try disabling it in your system (link: [http://ubuntuforums.org/showthread.php?t=6841](http://ubuntuforums.org/showthread.php?t=6841)) and see if that solves some of your problems. Also .doubleckick.net *is* the default for the 'network.dns.ipv4OnlyDomains' setting.

---

