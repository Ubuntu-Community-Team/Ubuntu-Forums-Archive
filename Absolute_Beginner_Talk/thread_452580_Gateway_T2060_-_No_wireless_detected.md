---
title: "Gateway T2060 - No wireless detected"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by criminalrodeo on 2007-05-23
I just bought a Gateway T2060 and it came bundled with Vista, which I liked, until it came time to find software to rip dvds and convert aac files. Anyways, threw 7.04 Feisty Fawn on, and tried to set my wireless card up. My computer's Wireless icon is next to the touch pad, and it's lit, which I thought meant it was going to work; it is a Realtek 8185. But when I open System> Admin> Network, I can see a "Wired" connection, and a "Modem" connection. The wireless doesn't even show up!

I've looked, and I cannot find anything to help me.

So, computer's hardware wifi icon is lit. Realtek 8185 card. Can't even see the "Wireless" connection in Network Tools.

Please help me out, really don't want to go back to windows.

---

### Post by dstew on 2007-05-23
I think there is no native linux driver for that card, but it works well using the Windows driver and the Linux utility called ndiswrapper. The utility "wraps" a windows driver with a Linux interface that allows you to use it. It can be a little intimidating for a new Linux user to get it to work, but there is a lot of help on the forum. Here is a thread showing the efforts of one determined user to get his 8185 to work:[http://ubuntuforums.org/showthread.php?t=191776&highlight=realtek+8185](http://ubuntuforums.org/showthread.php?t=191776&highlight=realtek+8185)

You can download the ndiswrapper-utils package from the [Ubuntu Packages]("http://packages.ubuntu.com/feisty/") site, and copy it over to your Ubuntu desktop. Right click and install. You might also need to get the ndiswrapper-common package too. If you have an internet connection by cable, just use the Synaptic package manager to get ndiswrapper.

---

