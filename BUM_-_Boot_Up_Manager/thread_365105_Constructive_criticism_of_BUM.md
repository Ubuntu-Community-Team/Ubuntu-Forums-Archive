---
title: "Constructive criticism of BUM"
date: 2007-02-19
forum: BUM - Boot Up Manager
---

### Post by CaptSaltyJack on 2007-02-19
OK.. the author of the program probably reads this, so I'll put this as tactfully as possible.  BUM is.. well... doesn't work so great.  Here's the deal:

From a UI perspective, it's confusing.  The whole lightbulb/checkbox thing, I don't get.  Which one is actually disabling the service from booting, and which is actually just shutting it down temporarily??  It's not too intuitive.  Plus, it doesn't pick up all services properly.  I installed mysql, and no matter how much I told BUM to stop or start mysql, it kept running.. and there was a "?" instead of a light bulb.  Weird.  I also installed ssh, which doesn't appear at all in BUM.

BUM could probably take a few pointers from Kubuntu's "System Services" (see attachment).  This app is perfect.. it lets me clearly know which services are running and which aren't, AND tells me if it's set to start at boot or not..and I can easily change any of those settings.  Plus it picks up a TON of services.

There's my two cents.  I hope to see BUM mature a lot in upcoming Ubuntu releases!

---

### Post by 16777216 on 2007-02-28
I like BUM but I must agree.
After using BUM GDM and KDM are acting strange refusing to start, refusing to log me in...

With GDM it starts fine but I have to log in then it hangs so I kill X ( Ctrl+Alt+Bksp ) then it works fine with the exception of I am unable to configure GDM unless I reinstall it then it still resets on reboot only to need reinstall all over again.

KDM, well thats *better *but I have to kill X ( Ctrl+Alt+Bksp ) as soon as I see my mouse cursor for it to start properly else it simply goes to a blank screen with a tty text cursor blinking in the top left corner.

As far as I can tell it is a X related server misconfiguration that I caused with BUM somehow. :confused:

---

