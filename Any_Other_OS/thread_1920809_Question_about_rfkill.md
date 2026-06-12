---
title: "Question about rfkill"
date: 2012-02-05
forum: Any Other OS
---

### Post by BarnOwl on 2012-02-05
I know I'm using Mint and posting in an Ubuntu forum but, they are pretty close cousins and I did post in the Mint forum first :)

This is an HP Probook 6560 with a Broadcom BCM43224 network card and I've been through just about every thread there is regarding drivers but, I'm coming to the conclusion that the driver isn't my problem.

This laptop does have a wireless button but, it looks like the wireless is bocked no matter what I do with it.  Here's what it does:

```
> rfkill list all
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

Press wireless button

> rfkill list all
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

Turn wireless button off in BIOS.

> rfkill list all
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes


```

As expected pressing the button with it turned off in the BIOS has no effect. rfkill unblock all/wifi/wlan has no effect.

My thinking is that drivers aren't going to effect that phy0 hard block.  Is that correct?  If it is correct, what should I be looking at?

I'll keep digging if it can be drivers but, I would hate to be looking in the wrong place.

---

### Post by Perfect Storm on 2012-02-05
Moved to Other OS/Distro Talk.

---

### Post by BarnOwl on 2012-02-05
No objection to the move but, I wouldn't have posted about this in an Unbuntu forum, if I thought the problem was peculiar to Mint.  I'm pretty sure it's not.  I guess I'll have to load 11.10 to prove that.

---

### Post by Perfect Storm on 2012-02-06
> **BarnOwl said:**
> No objection to the move but, I wouldn't have posted about this in an Unbuntu forum, if I thought the problem was peculiar to Mint.  I'm pretty sure it's not.  I guess I'll have to load 11.10 to prove that.

Doesn't matter. All distros that aren't in Ubuntu family goes to "Other OS/Distro Talk" forum.

---

