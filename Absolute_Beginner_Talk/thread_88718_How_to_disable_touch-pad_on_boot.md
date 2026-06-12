---
title: "How to disable touch-pad on boot?"
date: 2005-11-10
forum: Absolute Beginner Talk
---

### Post by NeoRc on 2005-11-10
I download an app called gSynaptics to control the touch-pad, and it works well. But when the PC boot again, the touch-pad auto enabled. I have browser the xorg.conf, but cannot find anything useful.

I'm new to Ubuntu, and new to Linux, thx for any suggestions.

---

### Post by bryan986 on 2005-11-11
In the synaptics touchpad part of the xorg.conf, try

```

   Option "MaxTapTime"                 "0"
   Option "MaxTapMove"                 "0"

```

---

### Post by NeoRc on 2005-11-12
[QUOTE=bryan986]In the synaptics touchpad part of the xorg.conf, try

```

   Option "MaxTapTime"                 "0"
   Option "MaxTapMove"                 "0"

```[/QUOTE]
It just diable the tapping, but the cursor still can move. And if I wanna enable the touch pad again, it's inconvenience.
Look at this screenshot below, can I simply disable the touch pad, and I can enable it by just one click at any time?
[IMG]http://us.a1.yahoofs.com/users/432a321bz704ed586/e78a/__sr_/e300.jpg?phgeZdDBzCWTdYkj[/IMG]

---

### Post by NeoRc on 2005-11-12
There's something wrong with my screenshot, upload it again:)
With the app called gSynaptics, I can simply enable or disable the touchpad by just one click. But the default status of the "Enable Touchpad" is checked. That's means when the system boot again, the touchpad is enabled again. All I wanna do is to just make it unchecked.
[IMG]http://img500.imageshack.us/img500/3292/e3005yj.jpg[/IMG]

---

