---
title: "Anyone using a KVM switch w/ two monitors?"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by garyed on 2008-03-17
I've been unsuccessful so far getting it to work.
Aluratek AKSP04 -  4 port KVM switch with Gusty & XP on dual monitors.
Anyone have any success please give me some info.
Thanks

---

### Post by Cypher on 2008-03-18
Correct me if I'm wrong but that KVM will only support a single console keyboard, mouse and monitor. Up to 4 machines can be suported with one of the about console devices. To have two monitors, you'd need a lot more expensive KVM.

Additionally, if you're only going to manage 2 PC's, and if you already have 2 monitors, then the KVM is overkill..a multi-station KVM makes sense when you're manging lots of PCs..

---

### Post by chcarver on 2008-03-18
I'm running the IOGear GCS1734 KVMP switch with 2 Ubuntu and 1 Windows XP configured.

The only problem I have is on reboot/boot-up Ubuntu must query for a screen resolution. If the KVM switch is on a different terminal Ubuntu automatically defaults to 800x600 resolution. Not sure if that is the default or what the KVMP switch is replying to. I can not set the resolution higher after the fact after boot up. So I have to make sure the switch is on the Ubuntu PC when it boots up to gather the proper monitor resolution.

---

### Post by garyed on 2008-03-18
> **Cypher said:**
> Correct me if I'm wrong but that KVM will only support a single console keyboard, mouse and monitor. Up to 4 machines can be suported with one of the about console devices. To have two monitors, you'd need a lot more expensive KVM.

Additionally, if you're only going to manage 2 PC's, and if you already have 2 monitors, then the KVM is overkill..a multi-station KVM makes sense when you're manging lots of PCs..

I probably should have explained my set up a little better.
I'm only using one monitor on the KVM switch with  three computers all dual booting.

1 - Feisty &  XP  
2 - Edgy & Win98  
3 - Gusty & XP ( A second monitor is hooked up directly to  this computer & not on the switch) 

Computer  # 1 works with no problems as long as its hooked up to KVM port -1
Computer # 2 can not configure the monitor higher than 800x600
Computer # 3 works with the monitor hooked to the KVM switch but the second monitor hooked up direct to it does not.

Using the exact same set-up, all three computers work perfectly if I boot them to Windows &  comp # 3 works fine with dual monitors(one on the KWM switch & one not) .  Booting into Ubuntu is where all the problems start. If I take my one monitor off the KVM switch & copy one of my backup xorg.conf files comp # 3 will work fine with Gusty & dual monitors. If I put my one monitor back on the KVM then Gusty will not detect either monitor & I have to copy the original xorg file back to get into my desktop.
Comp # 3  is used as a DAW & is really the only one I need dual monitors on.
I am hoping to use Ubuntu Studio & ween myself off of Windows completely.  
I hope I made things a little clearer now.

  

I've tried every solution I could find & nothing has worked so I came to the conclusion that the KVM manufacturers are missing something that Linux needs in their design.  

Comp # 3

---

