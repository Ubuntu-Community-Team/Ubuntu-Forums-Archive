---
title: "Portscan response"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by lawsonro on 2007-04-28
I have been using Ubuntu for a few months now (finally dumped XP, woo-hoo!) and just recently upgraded from Edgy to Feisty.  One of the sites I routinely use to check out my system is grc.com's ShieldsUp! I have Firestarter running and disabled ping response in /etc/sysctl.conf and before the upgrade I passed their test in full stealth mode. But now, it reports that only the poplular ports (smtp, http, ftp, etc) are stealthed -- everything else is reporting back to them as existing, but closed.  I thought at first it may have reverted sysctl.conf, but no, the site says I am still not responding to ping requests.  What changed?

---

### Post by Austin_KW on 2007-04-29
The port scan will scan your ports by attempting to open a tcp connection. If they are not stealt'ed it means that your pc is sending back a reject response. Check the advanced options in firestarter. You want the option to drop silently.

---

### Post by lawsonro on 2007-04-29
Right, that's exactly how it's set and always has been.  Like I said, the only change I have made at all is to use the auto-upgrade to Feisty.  No changes to Firestarter or network settings or anything else.  And as far as I can tell from the site, they haven't changed anything about their scan method to account for the result.  Could the new distro have some default setting over-riding the Firestarter options? I don't recall having to disable or reset anything when I originally installed Firestarter with Edgy, but the whole OS install process was so simple, maybe I'm forgetting something now that an upgrade reverted back?

---

### Post by lawsonro on 2007-04-29
What?!?  Just after posting my last response I went back to the site and ran another scan -- they now report as fully stealthed again.  Like I said, I use this site on a regular basis.  That used to be once a week with XP, in conjunction with anti-virus and spyware scans; now maybe closer to monthly. I just ran it today because I thought, hey, I hadn't done so since the upgrade early in the week.

When I ran it earlier, the quick-scan of common (couple dozen) ports reported what I outlined above. I ran the "full" scan (does every port up to 1056) and it started to show the same, so I aborted it.  Now, after getting full stealth on both again, I was reading the full results at the bottom of the page (hadn't done that in a long time -- hey I was passing with flying colors) and there is a section at the end, "Strange Results?", that talks about "adaptive" firewall behavior. It gives an example of a fullscan which starts out reporting closed and then changes to stealth.

They say "this can occur when a firewall "adapts" to the scanning IP and raises its defenses against just the attacker." Maybe that's what happened, but if so, it's the first time I've ever seen it. I had Zone Alarm on XP and Firestarter was the first package I custom installed on Ubuntu and they both have always been fully stealth before.

Does Firestarter apply "adaptive" methods? If so, could network congestion have slowed things down just enough that it did not instantly recognize that it was being scanned that one test?

Anyway, I guess mystery solved? Thanks for the reply, and I'll keep an eye on this awhile.

---

### Post by Catsworth on 2007-04-30
Hey Guys,

I seem to be having the same issue here.

Firestarter is sent to drop all packets silently, but the scan at [www.grc.com](www.grc.com) is showing responses from closed ports.  Would appreciate some help in getting this sorted.

Thanks.

---

### Post by OrangeCrate on 2007-05-06
Same problem here. I've come to the simple conclusion that the scan problem is at GRC's end.

---

### Post by Catsworth on 2007-05-06
How did you reach that conclusion?

GRC.com has always been very reliable, and the mechanism behind the search is simplicity itself - very little that could (or would) go wrong.....

---

### Post by OrangeCrate on 2007-05-09
> **Catsworth said:**
> How did you reach that conclusion?

GRC.com has always been very reliable, and the mechanism behind the search is simplicity itself - very little that could (or would) go wrong.....


Sorry, I've been out of town. Just checking recent posts. When I first revisited this thread a half an hour ago, I ran Shields Up!. Stealth failed. I just ran the test again, a half an hour later, and it passed. So what changed in a half an hour?

Now to answer your question directly... Frankly, I put more trust in iptables and Linux, than I do in an outside site, that was primarily written for Windows.

---

