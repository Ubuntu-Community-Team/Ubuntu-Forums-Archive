---
title: "Disappearing Modems in Dapper"
date: 2006-07-21
forum: Apple PPC Users
---

### Post by Ikkakujyu on 2006-07-21
Sooo.... I happen to be one of those people who are still using dialup access for the Internet. I have two Macintosh machines, a 500mHZ Dual-USB iBook G3, and a 400mHZ G4 tower. The two machines both use hardware modems attached to an internal serial port, and the modem has always shown up on /dev/ttyS0. With the latest release, however, the modems won't work, and probing /dev/ttyS0 comes up with an input/output error.

Is there any sort of workaround that nobody's telling me about?

I must stress that these modems *do* work in Ubuntu Breezy, and that they're certainly *not* softmodems, but hardware serial modems attached internally. OOTB support has disappeared in 6.06. and I've noticed the same problem in Fedora Core 4.

---

### Post by RHTopics on 2006-07-21
You are right, modem support in Dapper is different than Breezy.

I don't use the modem in my iMac G3 350mhz, but I could find it in Breezy by doing the following:

```
Open a terminal window
type "wvdialconf /dev/null" at the prompt
```

That does not work in Dapper.  Found this link that may provide a solution to your problem.

[http://www.ubuntuforums.org/showthread.php?t=196327](http://www.ubuntuforums.org/showthread.php?t=196327)

---

