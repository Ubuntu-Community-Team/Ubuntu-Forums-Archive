---
title: "gibson results for ubuntu ultimate"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by pdlethbridge on 2007-08-16
I got this message after I checked my computer at shields up. Now the computer is totally stealth and secure except for this. Can I change this? do I need to?

Ping Reply: RECEIVED (FAILED) — Your system REPLIED to our Ping (ICMP Echo) requests, making it visible on the Internet. Most personal firewalls can be configured to block, drop, and ignore such ping requests in order to better hide systems from hackers. This is highly recommended since "Ping" is among the oldest and most common methods used to locate systems prior to further exploitation.

---

### Post by por100pre1 on 2007-08-16
Is your PC behind a router? If so you need to configure your router's firewall settings. Otherwise install Firestarter, a tool for configuring your firewall:

```
sudo apt-get install firestarter
```

[Here's]("http://www.fs-security.com/docs/interface.php") how to use it. Close Firestarter when finished. **The firewall doesn't need Firestarter tool running to work.** Hope this helps. :)

---

### Post by pdlethbridge on 2007-08-16
Firestarter is installed but I get the same results after a reboot. I have roadrunner.

---

### Post by Arthur Archnix on 2007-08-16
But do you have a router? If so shield up is probably just testing your router, which is set to respond to ping requests. You could have a win95 acer and still be completely stealthy.

---

### Post by por100pre1 on 2007-08-16
> **pdlethbridge said:**
> Firestarter is installed but I get the same results after a reboot. I have roadrunner.

You should configure your router's firewall then. If you provide your router's brand and model maybe somebody here will help you. :)

---

### Post by pdlethbridge on 2007-08-16
I've uninstalled firestarter as I was not getting any better results. Ubuntu, by itself seems pretty secure. I'll see what I can do with the roadrunner supplied router. Thanks

---

