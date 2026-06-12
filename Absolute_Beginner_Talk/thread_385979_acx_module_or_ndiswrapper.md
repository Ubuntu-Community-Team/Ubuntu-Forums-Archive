---
title: "acx module or ndiswrapper?"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by Angry penguin on 2007-03-16
I was just wondering if anyone uses ndiswrapper with their acx111 chipset wireless cards? If so, does it work well, any probs, etc...

Only reason I ask is that I am using the acx module that comes with ubuntu and I noticed that things load slower in ubuntu than they do in windows. Its just not quite as snappy for some reason. :-k

---

### Post by Kobalt on 2007-03-16
I have an acx111 chipset based card and my download rates are about the same in win and Ubuntu. 
Maybe you refer to Firefox's speed : it is a bit faster on win than on Ubuntu, that's known...

---

### Post by Angry penguin on 2007-03-16
well, I was talking about when I open up firefox or navigate to a new page, its faster in windows.

---

### Post by zanglang on 2007-03-16
If you use wifi encryption I'd use ndiswrapper (acx does not even implement it),  plus NetworkManager only works with nidswrapper. It was a little troublesome to get it working at first, but has been working beautifully all these months. ;)

---

### Post by peterdm on 2008-07-22
Depends which authentication/encryption you want. In theory: use acx if you need WEP encryption. Use ndiswrapper or the experimental acx driver if you need WPA authentication. Unfortunately in practice, there are bugs preventing to get any of these solutions to work properly. These are my findings: 

The default acx module only supports various flavors of WEP but no WPA. Although some threads suggest otherwise, this even works in conjunction with NetworkManager. Whatever you do in this case, don't try to set this to WPA because it will freeze your system! [http://ubuntuforums.org/showthread.php?t=852225]("http://ubuntuforums.org/showthread.php?t=852225")

If you want WPA, you could use ndiswrapper, but even there is a weird bug in the ndiswrapper driver which causes authentication to fail. It works as long as a wired eth0 is plugged in as well, an it continues working after I unplug the wired cable, but it does not seem to work when bootstrapping from wireless only. Remember that you need to install the correct windows drivers as well!

As an alternative for WPA, there is a newer version of the open-source ACX driver [http://acx100.sourceforge.net/wiki/ACX]("http://acx100.sourceforge.net/wiki/ACX"), the experimental driver is the one that starts with ```
acx-mac80211
```. There is however no binary for it and you need to compile it yourself. In my case it doesn't compile because there is some struct in the kernel headers that mismatches the expectations of the module.

So bottom line: WEP works but WPA is broken, although there are 2 solutions that should theoretically work.

---

