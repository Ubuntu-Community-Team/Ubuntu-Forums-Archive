---
title: "Whoops, :("
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by Comzee on 2007-05-29
Ok, so  I upgraded to 7.04 and there is only one thing I would like to know. When I booted into Ubuntu for the first time after the upgrade it didn't detect my wireless card. It's a realtek card. Did they stop supporting that wireless card on 7.04, and can anybody give my a link to see what wireless cards are suppirted on 7.04. Thanks in advance, :D:D:D:D.

---

### Post by Ek0nomik on 2007-05-29
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by Comzee on 2007-05-29
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek")

That link (above) says it works "out of the box" with edgy but what about Feisty Fawn?
Can anybody give me a link to a Linux driver for a realtek wireless card?

Any help on this would be greatly appreciated.

---

### Post by Ek0nomik on 2007-05-29
Well, my wireless card didn't work out of the box either.  I had to do some tweaks for it.

I had never heard of RealTek cards until your post.  Does it have a version or model number?  There are a lot of threads for Broadcom 1300 etc, so having a number for yours would make finding support easier.

Talk to you soon.  ;)

---

### Post by Comzee on 2007-05-29
All I know is the full name which is as follows, "Realtek RTL8185 Wireless LAN Network Adapter"
It's a G/B integrated wireless card.
Hope that info helps, thanks for the help so for, <:-)

---

### Post by Ek0nomik on 2007-05-29
Ok, I hopefully have found some gold treasures for you.  :)

[http://ubuntuforums.org/showpost.php?p=2711549&postcount=229](http://ubuntuforums.org/showpost.php?p=2711549&postcount=229)

In the post, this user links to:

[http://ubuntuforums.org/showthread.php?p=2711528](http://ubuntuforums.org/showthread.php?p=2711528)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78255](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78255)

This apparently helped him/her get his working (it looks like he/she has the exact same card as you)

Good luck!

---

### Post by Comzee on 2007-05-30
Thanks for the links, :D:D:D:D:D:D. 
It sounds moderately hard to fix so I'll get back to this later and let you know how it works.
Thanks again.

Oh, and thank God for duel boot into Windows. :D

---

### Post by Ek0nomik on 2007-05-30
Well, my wireless card wasn't supported out of the box either.

When I first installed Ubuntu getting my wireless to work was one of my first projects.  It seems daunting at first, but once you get the hang of it, you can do it forever.

Give it a try, I bet you will find it easier than you would have originally thought.  ;)

---

### Post by Outrunner on 2007-05-30
Nah, doesn't seem hard to me! You simply have to edit /etc/modprobe.d/blacklist so type in the terminal:

```
gksudo gedit /etc/modprobe.d/blacklist
```
or ```
kdesu kate /etc/modprobe.d/blacklist
``` if you're using Kubuntu.

Then there should be a line that says

```
blacklist rtl818x
``` so simply put a # before it

```
# blacklist rtl818x
```

The rest should be easy

---

### Post by Comzee on 2007-05-31
Thanks to Ek0nomik and Outrunner for the help. I didn't have the "rtl818x" in the blacklist but I did have this,

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187

Close enough, so I put "#" in front of both "blacklist r818x" and "blacklist r8187".

Rebooted/

Then I put an "x" as the last latter in my ESSID.

Now I'm posting this in Ubuntu, again thanks for  the help. :D

---

### Post by Outrunner on 2007-05-31
Yay, glad it worked out for you!

---

