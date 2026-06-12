---
title: "Windows network and Firestarter"
date: 2006-01-01
forum: Absolute Beginner Talk
---

### Post by Gimbo on 2006-01-01
I've installed Firestarter, and I haven't messed around with any of the settings. I'm not sure whether it starts up automatically when I log in (I haven't added it manually to System>Preferences>Sessions>Startup Programs), but I assume it must do because it's preventing me from accessing shared folders on my local network (one other computer with Windows XP Home, connected with ethernet cables and a D-Link router). **When I stop Firestarter temporarily, I can access the shared folders**.

1. What settings do I need to change on Firestarter so it allows access to the shared folders? (If I need either computer's IP address, please give a brief explanation of how to find this out)

2. Could someone please just confirm that Firestarter **is** loading at startup?

---

### Post by Suger on 2006-01-01
2 - Firestarter (well, no, in fact, iptables...) is loading at startup.
1 - Open Firestarter, look what connections it blocks from the other boxes, allow them and there you (should) go.

---

### Post by Gimbo on 2006-01-01
Excellent, that worked a treat! For anyone who stumbles upon this thread later, the solution is as follows:

1. Have Firestarter open, with status set to "Active"
2. Go to Places>Network Servers
3. Click on "Windows Network" (if this doesn't show up, then you've probably got a different problem)
4. Click on the "Events" tab in Firestarter.
5. Right click the new "Blocked Connections" item and click "Allow Connections From Source".

Thanks very much for your help :)

---

