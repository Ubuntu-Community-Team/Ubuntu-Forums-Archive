---
title: "Hoary Hedgehog to Dapper Drake?"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by LinuxLove on 2006-06-20
Hey everyone,
I got a new computer recently and downloaded the Dapper Drake cd and burned the image onto a CD. I then restarted the computer, and tried to install Dapper. For some reason, the installation just freezes in place. There is no sound of my computer processing the CD and I'm stuck looking at the Ubuntu logo.

So I found my old Hoary Hedgehog cd. This time the installation worked perfectly. However, I'm having troubles upgrading. Can someone explain exactly how I can get to Dapper Drake? In Software updates ( gksudo "update-manager" ) it says that it cannot upgrade 'linux-image-386' or 'linux-restricted-modules-386'

Is there any way without me having to download and burn a disc? I really don't want to, seeing as the last time I tried it didn't work.


Thanks.

EDIT: I had to scramble on Google to find "https://wiki.ubuntu.com/BreezyUpgrade" -- So, now that I'm currently upgrading to Breezy, getting Dapper should be a breeze. ;)

---

### Post by trommelhawks on 2006-06-20
I newer used Hoary, but as fas as I know you have to upgrade to Breezy first and then to Dapper.

---

### Post by Gustav on 2006-06-20
It is not supported to do an upgrade Hoary->Dapper. But it is supported to do a Hoary->Breezy and then Breezy->Dapper.

Look at this [https://help.ubuntu.com/community/DapperUpgrades#head-b6c6f1f331471e88b2a2de46175ac1e676edd48d](https://help.ubuntu.com/community/DapperUpgrades#head-b6c6f1f331471e88b2a2de46175ac1e676edd48d)

---

### Post by muep on 2006-06-20
Have you tried Dapper's Alternate install cd? It works similarly to Hoary's install.

---

### Post by FredB on 2006-06-20
Yes, it works the same way hoary and breezy for installation. The best thing to do is to backup /home directory and upgrade to dapper ;)

---

### Post by LinuxLove on 2006-06-20
Hey again,

Trying to upgrade from Breezy to Dapper wasn't exactly what I expected. I ran into several errors, and when I tried to reboot my system it simply would not let me login (login screen did not appear; instead, ONLY the text "login:" appeared)

I then burned the alternate cd. After installation and before the system reboots into ubuntu, I'm prompted on a black screen with two white bars. For some odd reason, I'm just frozen there. I can't do anything at all, so I figured it was still configuring files or something. I took a nap, woke up about 6 hours later and, sure enough, theres the black screen. Still there.

For some reason I think dapper just doesn't like my system. Although previous versions of Ubuntu have worked flawlessly, I'm just not getting why I can't install dapper.

(System specs: 2.9 Ghz Pentium 4 (x86) - 512mb Ram - Integrated Card - HP Pavillion a818n)

---

