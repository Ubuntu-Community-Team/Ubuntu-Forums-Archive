---
title: "1st Gen Macbook Wifi issues"
date: 2008-03-27
forum: Apple Intel Users
---

### Post by cariad on 2008-03-27
So, I am assuming that this has come up at least once before.

I am moving from Backtrack to Ubuntu due to Ubuntu's better fan support (though, I like BT's ease of use and toolset) and cannot seem to get my wifi drivers correct. When I run a "sudo airmon-ng stop ath0; airmon-ng start wifi0" in BT, I get another ath0 which is ready to go for injection. In ubuntu, I get an error stating that there are permissions problems. I have this feeling it relates to the fact that I am using sudo WAY too much to run things, but, I'm starting to get fed up.

Does anyone have experience getting some of the tools from BT3 for the rt73 and ath chipsets working?

Thanks!

PPS: Also, everytime I scroll down or up in Firefox with two fingers, it sends me random places. Go figure.

EDIT: Forgot to edit the FF config, fixed the pad problem! Ubuntu has much better pad support.

---

### Post by cyberdork33 on 2008-03-27
I don't even know what those tools are....

What hardware do you have? A broadcom or atheros card?

---

### Post by cariad on 2008-03-28
It's an Atheros card.

The tools are for wifi analyzation and cracking. I think BT's wiki has a complete tool list, but I need only a small fraction of them.

---

### Post by cyberdork33 on 2008-03-28
you didn't have a sudo on the second command.

---

