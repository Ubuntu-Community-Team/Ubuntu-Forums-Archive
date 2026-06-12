---
title: "xserver won't start:&quot;(EE)device not found!&quot;"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by DustRatt on 2007-03-20
so, i have tried to install edgy several times now and the same, cryptic "no screens found" shows up after xserver fails to start. at the end of the error report it says that it can't find my video card(ati Radeon X850XT) 

"[I](WW) ATI: PCI Mach64 in slot 1:0:0 could not be detected!
(WW) ATI: PCI Mach64 in slot 1:0:1 could not be detected![/I]"

idk why it has an older graphics chip-set there... that im not using...
ive tried reconfiguring xserver but i think the pci address is wrong and i don't know how to get the correct one. help would be appreciated.

---

### Post by benfindlay on 2007-03-20
I take it you are just dumped at a command line and asked to log in then?

If so, then log in, then type the following:

```
sudo dpkg-reconfigure xserver-xorg
```

This command allows you re re-set-up X on your machine (the GUI)

If you follow the on screen instructions and read eerything there, you can't really go wrong. It will also attempt to auto-detect most stuff for you if you let it

Hope this helps!

---

### Post by DustRatt on 2007-03-20
i have done that[launch the xserver reconfig.]. i did that before i even made the post. i was asking how to find the correct pci address for my video card. the content of the error message has led me to believe that the address supplied was incorrect. i have also tried to check the address w/ "*lspci -x*" and it came back with 1:00:0 and 1:00:1, the same locations the error said it was not in.

---

