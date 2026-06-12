---
title: "Asus eeePC R11CX resolution fiasco"
date: 2012-04-27
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Malcolm Isaacson on 2012-04-27
Hey everyone,

First off: this is the first time I'm posting here, and believe me, I'm doing it as a last resort. If the subject's been discussed (which it has) and a solution was found (not to my knowledge), please excuse me.

Here's the deal:

My netbook's* display's EDID is not communicating well with the system, thus limiting its resolution at 800x600, even though both the graphics chip (Intel GMA 3150) and the display support 1024x600.

I've tried everything I could think of, including messing with xrandr, the xorg.conf file, live booting Puppy Linux and Fedora, etc. On all instances, the only possible resolution is 800x600. Except on the preinstalled Windows 7 distribution, which is doomed to be erased.

Here's the lspci output [excerpt]:
```
user@R11CX:~$ lspci
00:00.0 Host bridge: Intel Corporation Atom Processor D2xxx/N2xxx DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller (rev 09)
```

And the xrandr output:
```
user@R11CX:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
  800x600         0.0* 
```

Should the need arise, I will gladly add any additional information.

Thank you very much!

*_[Asus eeePC R11CX]("http://www.steg-electronics.ch/fr/article/asus-eeepc-r11cx-black-671190.aspx")_ - click on "caractéristiques techniques" to view its specs.

---

### Post by Malcolm Isaacson on 2012-04-28
anyone?

---

### Post by Thomas Do on 2012-06-05
I found that: [https://answers.launchpad.net/ubuntu/+faq/1901](https://answers.launchpad.net/ubuntu/+faq/1901).

---

### Post by Malcolm Isaacson on 2012-06-05
Thank you!

But the procedure comes short at its first stage already; I don't know my monitor's HorizSync and VertRefresh.

I'll dig into it tough. In any case, thanks for your reply!

---

### Post by ernz on 2012-06-19
I'm having the exact same issue with my Samsung N102SP Netbook - same chipset:

Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics

Any solution yet?

---

### Post by Malcolm Isaacson on 2012-06-19
Still not... sorry

---

### Post by wms on 2012-06-20
+1

ASUS eee pc Intel D2xxx

Tried this but did not work: [http://forums.debian.net/viewtopic.php?f=7&t=78157&sid=d1fa8f640e457f72af26b45641bb66ef&start=15#p436455](http://forums.debian.net/viewtopic.php?f=7&t=78157&sid=d1fa8f640e457f72af26b45641bb66ef&start=15#p436455)

Will resintall Ubuntu again and start over.  If anyone finds the fix, could you please post it here?

---

### Post by jenhawk on 2013-01-27
Did you ever come up with a solution to this? I have the same Asus netbook model, just struggled for the last day to get Ubuntu installed, and now that it's working I have this same resolution issue. How in the world to get this HorizSync and VertRefresh info??

---

### Post by james1701kirk on 2013-04-08
Although I just have a Debian/Wheezy system here I wanted to let you know that I have Asus EeePC 1008 which also just brought up only a resolution of 800x600... After trying a lot of things I installed the latest grml-kernel (3.7-1-grml-amd64)[1], rebooted and finally got my full resolution of 1024x600.

[1] [http://grml.org](http://grml.org)

If you need any help installing the grml-kernel please let me know.

---

### Post by fantab on 2013-04-25
I have asus 1015CX cedartrail. I have found that fedora18 works in its default install. I have installed fedora_xfce 32bit. Everything worked out of the box.

---

