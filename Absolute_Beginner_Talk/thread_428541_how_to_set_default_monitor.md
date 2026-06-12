---
title: "how to set default monitor"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by treeby on 2007-04-30
i made the mistake of installing feisty with two monitors...a small like...14 inch monitor and a big
20" wide screen. for whatever reason ubuntu decided that my small one would be default and whenever
i use that new cool nvidia configuration and make the big monitor the one i want to use, and then save it
in the xorg file, when i restart, i'm back to the small monitor again....or worse...
sometimes i don't have window borders, no text shows up in the terminal or i get a black screen....
i'd be happy if i could just use my big monitor normally...is there any way to set it so i can use it?
i have a geforce7600GT, core2duo and beryl installed...could it be beryl's fault?

(when i run nvidia-settings i type something in like gksudo nvidia-settings)

---

### Post by nonewmsgs on 2007-05-06
the easy way to just use your big moniter is this unplug (from videocard) te small moniter
sudo dpkg-reconfigure -phigh xserver-xorg

and it should redo your xorg.conf file so it uses the big one.

---

