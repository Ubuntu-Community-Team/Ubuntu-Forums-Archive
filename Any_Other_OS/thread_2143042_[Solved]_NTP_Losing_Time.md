---
title: "[Solved] NTP Losing Time"
date: 2013-05-07
forum: Any Other OS
---

### Post by efriese on 2013-05-07
Cross posted in the Mint forums. I don't think that forum is as active at the awesome Ubuntu forums =)
[http://forums.linuxmint.com/viewtopic.php?f=18&t=133186](http://forums.linuxmint.com/viewtopic.php?f=18&t=133186)

I noticed yesterday that my Linux time was about 20 minutes slower than my Windows box. I restarted ntp and the time updated, but it's still losing time. I've tried adding more NTP servers in the conf file. I also read that I can rename the drift file located at /var/lib/ntp/ntp.drift and that would cause NTP to recalculate the drift. I performed the move and restarted NTP and there's not a new drift file. I've also seen some posts about problems with dual booting. This is a dedicated Mint box. Any ideas? I've tailed syslog and don't see any errors regarding NTP. The time does update when I restart NTP, so I don't think it's a firewall issue.

I'm running Mint 14 Cinnamon 64 bit.

Thanks!
Eric

---

### Post by tgalati4 on 2013-05-07
20 minutes is quite a bit of drift.  Dual-booting will usually cause an issue with local time zone versus GMT depending on what is stored in BIOS and what the operating system uses and syncs to at bootup.

In your /etc/ntp.conf file, you can change this line:

# Enable this if you want statistics to be logged.
#statsdir /var/log/ntpstats/

Remove the comment marker (#) to enable the statistics dump to /var/log/ntpstats.  Let it run for an hour then look at the the statistics to see what is happening.  If this is an older machine, you might need a new button battery to keep the correct time.

To get more information on how to drive ntp:

```
man ntp.conf
```

---

### Post by efriese on 2013-05-09
tgalati4, thanks for the response. I did enable the ntpstats and let that run for awhile. As I mentioned above, I moved the ntp.drift file and restarted the daemon. That didn't create a new file. To install a new fan I had to reboot the machine. Ever since the time has been right. I checked and there is a new drift file, so I'm thinking that was the problem. Thanks for the help!

---

