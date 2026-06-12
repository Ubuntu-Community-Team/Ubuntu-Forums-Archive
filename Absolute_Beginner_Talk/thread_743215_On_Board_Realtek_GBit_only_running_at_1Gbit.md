---
title: "On Board Realtek GBit only running at 1Gbit"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by foxbuntu on 2008-04-03
Sounds like you need to make sure autoneg is enabled, to do this:

```
sudo ethtool --change eth0 autoneg on
```

Then do the following:

```
sudo ifdown eth0 && sudo ifup eth0
```

This should force the interface to auto duplex speed (should pickup 100MB/Full) and then force the interface down and back up to pickup DHCP

---

### Post by mike farad on 2008-04-17
Auston,

 I too have the exact same problem, in fact I posted a similar thread on another forum:
[http://www.linuxquestions.org/questions/linux-newbie-8/on-board-realtek-gbit-only-running-at-1gbit-631712/]("http://www.linuxquestions.org/questions/linux-newbie-8/on-board-realtek-gbit-only-running-at-1gbit-631712/")
oh wait, that was my post.  Is this bad form to copy someone else's post?

Other than that, did you get yours fixed?

Mike

---

