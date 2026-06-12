---
title: "Booting problems on Kubuntu"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by buildsomethingcrazy on 2007-12-11
Well, I switch from Ubuntu to Kubuntu because I find that I like the KDE desktop better than GNOME.

Anyways, I got it to install after I waited a couple of months for the disc to reach my house. It ran fine, looked great, just seemed to run better than Ubuntu all together for my computer. After I installed it I brought my computer to a friends to LAN. I didn't bother bringing my monitor since he had a spare. Well, when I booted up Kubuntu and it was acting fine. The blue loader came up and then went to show me the GUI. I could even see the mouse cursor telling me it was loading up  (The little round thing with dots) then about two seconds of that it goes to the black screen and reads:

[SIZE="1"]Starting K Display Manager: kdm.
  *Starting Common Unix Printing System: cupsd                                     [OK]      /sys/devices/system/cpu/cpu01/cpufreq/scaling_governor: Directory nonexistant
  *CPU frequency scaling not supported
                                                                                                                  [OK]
  *Starting Avahi mDNS/DNS-SD Daemon avahi-daemon                          [OK]
  *Starting DHCP D-Bus daemon dhcdbd                                                   [OK]
  *Starting Bluetooth services                                                                   [OK]
  *Starting anac (h) ronistic cron anacron                                                 [OK]
  *Starting deferred execution scheduler atd                                           [OK]
  *Starting periodic command scheduler crond                                          [OK]
  *Checking battery state                                                                         [OK]
  *Running local boot scripts (/etc/rc.local)                                               [OK][/SIZE]

Now I get that problem every time I try to boot. I tried [SIZE="1"]sudo dpkg-reconfigure xserver-xorg[/SIZE] But, no luck. I noticed though it keeps thinking I have an Intel video card when I have an ATI. I have disabled the intergraded Intel through BIOS but, for some reason it's still picker it up. Could it still be confusing it? I was thinking about reinstalling but, I would like to figure out how to fix this problem so that I may learn how to fix it if it ever repeats.

Thanks.

---

### Post by lmlahti on 2007-12-23
I have a similar problem. For me the text stops in an earlier stage. The exact text reads:

Starting K display manager: kdm
 * Starting common unix printing system: cupsd

After this the screen turns into black, and computer does not react even to ctrl-alt-del.

I also have two graphics cards, and the integrated one has been turned off in BIOS.

Reinstallation does not seem to help. The same problem occurs with gutsy livecd and alternative-install-cd. With previous installations this problem has not occurred, now it seems to occur in all installation trials.

I would be delighted of any advice on this as I have no idea on how to fix this and get my computer work again.

b r
LL.

---

### Post by lmlahti on 2007-12-23
I was able to fix the problem by disabling parallel port in BIOS. It seems that in my case the problem really was in he printing system configuration. 

Unfortunately I don\t know whether this helps in the initial problem of this thread as there the machine is able to proceed a bit further. 

LL

---

