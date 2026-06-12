---
title: "Simple ntpd setup needed"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by lyna on 2007-04-16
Hi all,

I've been trying to set up a simple date service on one of my Ubuntu 6.06 systems.  All I want it to do is to pick up the date/time from an NTP server on another part of the network, then be available to provide it to other systems on my local network.  In essence, it will be both a client and a server.  For political reasons, I can't synchronise all my local servers to the other network.  I've been trying to wade through the documentation, but it's hugely complex and I find it terribly confusing.

I believe I will need to run the ntp server daemon on my local client/server so that it can pass the time to my local network systems.  Then I could just run a daily cronjob using ntpdate on the local clients.  However, if ntpd is running on my local server/client, I can't use ntpdate on it to pick up the time from the other network; it tries to use the same port as ntpd.  Is ntpd supposed to synchronise itself with the other network using ntp.conf?  I can't seem to get that to work.  When I run ntpd -q, I get a few errors in syslog, e.g. "Bad file descriptor".  All I've changed in the default ntp.conf file is the name of the server to use.

Does anyone have any suggestions?  Am I missing the point somewhere?  Is there a documentation site that provides "NTP for Dummies"?

Cheers,
Lyn  :confused:

---

### Post by ayenack on 2007-04-17
Follow this [http://www.ubuntugeek.com/keeping-your-system-clock-current-automatically-via-network-time-protocol-ntp.html]("http://www.ubuntugeek.com/keeping-your-system-clock-current-automatically-via-network-time-protocol-ntp.html")

---

