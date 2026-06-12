---
title: "Install network drivers"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by mjmjohn on 2007-04-26
Installed 7.04 in vmware server and everything seems fine except I have no network connectivity....hmmmm. Because I know  nnothing about linux I can't even find a way to check if the drivers for the realtek nic in the mobo loaded. Can anyone direct me where to find the "Device Manager" or something like it to check the nic? And if I am without the proper driver, how do I load it? Man, I feel like a babe in the woods here in Linux world

---

### Post by caffienefree on 2007-04-27
For future reference, Device Manager is System>Preferences>Hardware Information.

In the network options of the virtual machine you're using, select the "share nat" option. If you check this, it will share the same network connection that your host machine uses, so you dont need to install drivers for any network hardware.

---

