---
title: "tingWireless connection not shown in network settings"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by KC_HYPE on 2008-04-18
I 'm totally new to linux and just installed ubuntu on my macbook.
everything works fine except that in Network Settings it only shows a Wired and Modem Connection and not a Wireless one.

Any idea on how i can get my internet up and running would be greatly appreciated.

---

### Post by nicedude on 2008-04-21
You need to determine what chipset your wifi card uses first as it will make a big difference on what to do. You can figure that out with some googling of your PCs make & model combined with wifi chipset or wireless card. Once you figure out the wifi chipset manufacturer and model then google that combined with ubuntu driver or Linux driver and see what others say they used, even if they are talking about some other version of linux.

you might start by looking here at the macbook wiki page
[http://en.wikipedia.org/wiki/MacBook](http://en.wikipedia.org/wiki/MacBook)

In general here are a few driver solutions that are common for linux users to have to use.
1. madwifi drivers  -  3d party awesome drivers for Atheros chipsets ( this is what I use )
2. Ubuntu restricted drivers manager which supports some wifi chipsets
3. ndiswrapper  - which is software that allows you to use a windows based driver setup
.exe to install wifi drivers. even though you have a mac it still could have a chipset that 
also is sold as a windows card so don't count that out either ( I think )

There are some other more obscure hacked driver sources but if people are making your model's wifi work it is probably with one of the above methods. So start by finding out what you have and research the driver needed. If you get stuck after you find out what driver someone is using because you can't get it to install, then PM me and I will attempt to help you further.

Glad to see you kicked macos off your macbook as now it actually belongs to you.

---

