---
title: "Internet/Ethernet connection dropping"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by Copps on 2006-09-27
##This is a freshly installed ubuntu to a new machine, no additional software added, machine patches with listed software updates after first boot up##

After using firefox for a while (usually 5-10 minutes) my ethernet link goes down. At first I thought the system was hanging because everything (inc. mouse pointer) freezes. After hard rebooting and the same problem occurring again, I noticed I could still type to the command console.

I checked out /var/log/messages and have the following in there:

```
Sep 27 22:40:33 laptop1 kernel: [17180323.780000] tg3: eth0: Link is down.
Sep 27 22:40:35 laptop1 kernel: [17180325.780000] tg3: eth0: Link is up at 100Mbps, full duplex.
Sep 27 22:40:35 laptop1 kernel: [17180325.780000] tg3: eth0: Flow control is on for TX and on for RX.
Sep 27 22:43:01 laptop1 kernel: [17180470.804000] tg3: eth0: Link is down.

```

And this time it hasn't come back (posting this from another PC). The system freezes for about 5 seconds at a time, then works for 1 sec, then freezes ... the network connection icon in the taskbar shows as disconnected.

Anyo troubleshooting ideas? Or other log/system files that might point me toward a solution?

---

### Post by wieman01 on 2006-09-27
Just a thought... Have you tried another cable?

---

### Post by eekrazyk on 2007-02-07
I just started having this same problem and posted on the kubuntu forums

[http://kubuntuforums.net/forums/index.php?topic=13557.0](http://kubuntuforums.net/forums/index.php?topic=13557.0)

As I stated there, I had a working connection to my corporate LAN through a hub, but once I removed the hub, I'm having problems.  Anyone here have any ideas?

---

