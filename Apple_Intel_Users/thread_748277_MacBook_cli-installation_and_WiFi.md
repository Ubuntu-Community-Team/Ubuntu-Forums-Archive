---
title: "MacBook cli-installation and WiFi"
date: 2008-04-07
forum: Apple Intel Users
---

### Post by nielsb on 2008-04-07
So, I have a MacBook (DualCore, not DualCore2). I'm doing a cli installation from the Hardy mini.iso disk (the reason is that I want a very lean and mean installation). Everything goes OK, and I then install xfce on top of my cli - all good.

However, I cannot seem to get wifi to work. I install wifi-radar, and when I run wifi-radar I get the message that the "Interface doesn't support scanning: Network is down". Well, the network is not down as my other Ubuntu machines connects to the wifi network without problem. So I follow the instructions on the MacBook Wiki how to install the madwifi drivers. I take them down from svn, make, make install-modules all according to the wiki entry and no problems.

However, after reboot and re-running wifi-radar, I have the same issue. At the moment I'm stumped, and I don' know enough abut iwconfig etc, to know where to start looking. So, if anyone has any bright ideas, I'm all ears.

Oh BTW, if I install Ubuntu (or Xubuntu) straight from the live CD everything works just fine with my wireless. But as I said, I want a minimal installation to begin with.

Thanks!

Niels

---

### Post by Rog-Mahal on 2008-04-07
Your minimal installation probably doesn't include the right wireless module. Do a little research and find out what version your wireless card is. You probably need to install the linux-restricted-modules package that is compatible with your kernel version if it worked natively with the full ubuntu install. If you don't want to install that package because it includes some stuff you won't need, you might want to try and find the right madwifi driver for your card. You'd have to manually compile and install it, but that's not too hard.

Hope that helped, good luck!

---

### Post by nielsb on 2008-04-08
> **Rog-Mahal said:**
> Your minimal installation probably doesn't include the right wireless module. Do a little research and find out what version your wireless card is. You probably need to install the linux-restricted-modules package that is compatible with your kernel version if it worked natively with the full ubuntu install. If you don't want to install that package because it includes some stuff you won't need, you might want to try and find the right madwifi driver for your card. You'd have to manually compile and install it, but that's not too hard.
Thanks! However, I do actually have compiled and installed the module(s) for my card, and that was the point of my question. I compiled and installed and I still couldn't see my network(s).

However, after I wrote my original post, I installed network-manager-gnome and by doing that my wireless networks now became visible, and wifi-radar can also see them. So, the question is really what network-manager-gnome did, that I didn't do initially? :-)

Well, I'll plod along and see if I can sort this out.

Niels

---

### Post by cyberdork33 on 2008-04-08
don't you have to put Atheros cards in a "scan" mode to see AP's?

---

### Post by Rog-Mahal on 2008-04-08
oops! sorry, I guess I missed that line of your post. what kind of output does running iwconfig give you? Maybe that will give us a place to start.

---

