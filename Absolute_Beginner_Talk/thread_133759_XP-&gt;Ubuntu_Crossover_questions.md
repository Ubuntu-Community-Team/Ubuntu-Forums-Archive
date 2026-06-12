---
title: "XP-&gt;Ubuntu Crossover questions"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by DerGeist on 2006-02-20
Hi guys,

I installed Ubuntu a while ago and I love it. I just have a few things that are keeping me from making "the plunge" to going all-ubuntu. Let me first say I'd love to because I really like Ubuntu, the GNOME UI is so much better than windows. I searched the forums but did not find any posts that addressed these issues adequately.

So here they are:

1) I can't fit half as much stuff on the screen at once in GNOME as in XP. I think it is the font size, but even when I turn that down it still doesn't help much. I think it might be the toolbar size to some extent but it also seems like GNOME is rife with very LARGE icon buttons. Nice because they're hard to miss, but in XP i can comfortably fit Firefox, a GAIM chat window and my GAIM buddy list on one screen. In GNOME I can only fit one at a time onscreen (at the same window size in both OS's obviously). It sounds dumb but this really impacts my productivity while in GNOME because of all the context switching.

2) Repaint delays are slower in Ubuntu. This is especially noticeable in Firefox -- pages load but onscreen they appear much slower than in Windows. I have an ATI Radeon 9800 which may be the problem (or part of it) because I hear ATI's support for linux is pitiful. Any suggestions?

3) I don't think Hyperthreading is turned on in Ubuntu. I have a 2.8 GHz P4 with Hyperthreading but I don't think it is turned on because things seem to run slower in Ubuntu. How can I turn it on?

Thanks for your help. If you guys can help me solve these teensy little problems, I will finally be ready to "make the switch." I really love Ubuntu and Linux in general and would be very happy to make this change over.

Thanks,
DerGeist

---

### Post by el3ktro on 2006-02-20
Well you might want to turn off the text under the icons, so that you have only the icons displaying - and reduce the font size. Well in Gnme you have virtual desktops, they're a nice way to organize your desktop. I have one for browsing, one for IM/irc stuff, one for background tasks etc.

Yes Linux & ATI don't work good together. Did you install the latest ATI drivers? Open Synaptic and search for "xorg-driver-fglrx", install it, and replace the driver by "fglrx" in /etc/X11/xorg.conf. The major reason for Gnome's slowness is the window manager Metacity, this is sad yes, but help is on the way and soon - thanks to Xgl - Linux will be absolutely superior to Windows when it comes to graphics ... :-)

For hyperthreading: You won't likely notice any difference if hyperthreading is turned on or off. This is only usefull for applications with heavy threading, or when you run A LOT applications/processes in parallel. During the normal desktop operation HT is pretty useless, imho. But you can check if it is turned on: Open a Terminal & type "cat /proc/cpuinfo". If it shows you two processors, then it's turned on.

Tom

---

