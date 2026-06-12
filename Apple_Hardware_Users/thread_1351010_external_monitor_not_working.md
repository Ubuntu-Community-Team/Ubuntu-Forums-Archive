---
title: "external monitor not working"
date: 2009-12-09
forum: Apple Hardware Users
---

### Post by msto on 2009-12-09
Hi, I'm running Ubuntu 9.04 on a Macbook 4,1 and I can't get my external monitor to work correctly ([this Acer]("http://www.newegg.com/Product/Product.aspx?Item=N82E16824009145")). The laptop is closed so the external monitor is running as the only display, but I can't get it to display the proper screen resolution. The external should work at 1680x1050, but it defaults to 1024x768, and the highest option that Display Preferences gives me after I turn off the mirror screens preference is 1360x765. When I try to apply the new resolution, I'm told to log out and log back in, but whenever I do my monitor tells me that the new input is unsupported. Any suggestions on how to get my monitor working at the correct resolution?

Thanks!

---

### Post by linuxopjemac on 2009-12-10
I heard problems with the different cables. mini-DVI to DVI seems to sometimes work as opposed to mini-DVI to VGA. You might want to try the 'xrandr' tool to "turn on" the external display.

[http://mac.linux.be/content/set-xorgconf-manually-xrandr](http://mac.linux.be/content/set-xorgconf-manually-xrandr)

---

