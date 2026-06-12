---
title: "Procedure for installing new LCD monitor"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by rdilliker on 2006-10-14
I currently have a 17" Dell CRT monitor which I setup when I installed Ubuntu Dapper Drake. I just bought a Dell 2007WFP LCD monitor so I'm wondering what the right procedure is in Ubuntu for installing the monitor. Do I need to run xserver config or whatever myself before I plug in the monitor or what?

I have an nVidia 6600GT video card.

Thanks.

---

### Post by PriceChild on 2006-10-14
Unplug the old one... plug in the new one.

If this monitor has higher resolutions than the old then edit /etc/X11/xorg.conf accordingly.
or
```
sudo dpkg-reconfigure xserver-xorg
```leaving all options as they are but the resolution section. (spacebar selects, enter  moves to next page)

Pricey

---

