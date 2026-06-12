---
title: "XFCE + xrdp = trashed desktop theme and settings"
date: 2014-01-28
forum: Any Other OS
---

### Post by getut2 on 2014-01-28
Someone please help me. I'm running Mint 16 XFCE (based on Ubuntu) and have a  100% fresh install that I'm trying to set up as a Remote Desktop  terminal.


If I log in locally, everything is great and the  themed XFCE looks like it is supposed to, but if I log in with the same  user account with RDP via xrdp, the first time I sign in it asks me if I  want the default XFCE environment and it reverts to a 100 percent  default XFCE look. If I go back to a local sign in, it is now trashed  there also. I can  delete the ~/.config/xfce4 folder and then log back  in locally and the full theme is back.


If I just "go with it"  and spend the time to configure xfce once it has been trashed, then it  really gets weird. If I select the style and icon themes from the  appearance utility, it doesn't change anything in RDP, but if I go back  to a local sign in, I can see that it changed to the Mint stuff.


It  is like some component necessary to display certain things isn't  getting started when I log in via RDP. Anyone have any ideas?

---

### Post by Frogs Hair on 2014-01-28
***Moved to Other OS/Distro Support.***

---

### Post by steeldriver on 2014-01-28
There are some known issues with xfsettingsd over VNC/RDP e.g.

[http://askubuntu.com/questions/411782/xfsettingsd-crashes-due-to-missing-xi](http://askubuntu.com/questions/411782/xfsettingsd-crashes-due-to-missing-xi)

I don't understand your issue well enough to know if they might be related, but that would be my starting point

---

