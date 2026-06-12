---
title: "External monitor on Santa Rosa Macbook Pro"
date: 2007-11-10
forum: Apple Intel Users
---

### Post by matei125 on 2007-11-10
Hi,

I've installed Gutsy on my Santa Rosa Macbook Pro, and so far everything is working fine. However, I now want to use an external monitor (24 inch 1920x1200 Sun widescreen monitor). I've tried running xrandr as recommended in some tutorials but it doesn't list it - presumably the Nvidia driver doesn't support xrandr. The System > Administration > Screens and Graphics dialog detects it, and I can enable it there, but I haven't managed to set the resolution on both the external monitor and my main monitor correctly - it always ends up putting too high a resolution on my main monitor and then I have to scroll around to see the menu and such. The closest thing to non-brokenness that I've gotten is to run nvidia-settings and enable the monitor there with TwinView. This gives me a very large desktop spanning both screens, which works fine, but the problem is that Ubuntu tries to keep the same large virtual desktop size when I unplug my external monitor (even when I reboot without the monitor plugged in). Is there anything I can do to get the second monitor enabling/disabling itself in a "plug-and-play" manner or at least to have just my regular setup when I reboot and the second monitor is not plugged in?

PS I've been running Compiz, but I've also tried these things without it (with desktop effects set to Off) and I have the same problems.

---

### Post by thingy on 2007-11-10
To give you a better understanding of dual monitor setups, read this howto.

[http://gentoo-wiki.com/HOWTO_Dual_Monitors](http://gentoo-wiki.com/HOWTO_Dual_Monitors)

I am assuming you are using nVidia's TwinView feature and so I think the section: 
** Connecting a second monitor after X startup**


may answer your question.

---

