---
title: "Upgrade to Fiesty Screwed by boot"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by dryan93 on 2007-05-07
I was running Ubuntu Edgy Eft with absolutly no difficulty. I was away for about a month and when I got back Fiesty had been released. So I first updated Edgy with it's nessicary updates. And then I proceeded to upgrade to Fiesty. Now When I boot fiesty it get's through the first stage of boot (the orange status bar right after grub) and then when it reaches the login manager I don't even get an error message. Nothing is on my screen. Absolutly nothing. Is there a "repair mode" in Fiesty that is accessable from GRUB? I only have the standard boot option selected and Windows XP. I've been forced to use XP for the past 3 days. AHH

---

### Post by zvacet on 2007-05-07
It seems like video card problem.when grub shows up you can select where you want to boot.select recovery mode and type 

```
dpkg-reconfigure xserver-xorg
```

in case that you use **nvidia** replace it with **nv** .After that go and upgrade your drivers.If you use other dard choose **vesa** and when you get graphic search for proper drivers for your card.

---

### Post by Cypher on 2007-05-07
And if the "repair" option doesn't show up in GRUB, once you think the machine has booted up and the login screen should actually appear, hit CTRL-ALT-F1 to get the regular text console. Login and do the command in the above post with "sudo" added..

---

