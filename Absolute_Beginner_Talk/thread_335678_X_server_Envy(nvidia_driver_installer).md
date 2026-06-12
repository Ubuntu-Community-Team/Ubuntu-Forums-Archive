---
title: "X server Envy(nvidia driver installer)"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by bradsubarcadia on 2007-01-10
I used envy to install drivers for a legacy nvidia card I have (tnt2 64)  and it worked perfectly for about a week 

but today after I attempted to play soldat using wine X server restarted
when it restarted I didn't get an nvidia logo screen that usually precedes the ubuntu login screen I didn't think much of it and continued 
I tried soldat again and the same thing happened so this time I restarted the computer but when it booted up x server would not run the problem was something about Nvidia drivers not compatible(I'll get the exact message if necessary) 
I tired reinbstalling the drivers with envy but it still didn't start
I used the function ```
sudo dpkg-reconfigure xserver-xorg
```
and used vesa and X works
but then when I use envy to reinstall the nvidia drivers X won't start unless I don't let envy edit the Xorg.conf file (making the drivers useless) 
how can I get the drivers to work again

---

### Post by bradsubarcadia on 2007-01-10
The problem was resolved after I attempted the manual route(from the ubuntu wiki) which didn't work
then I tried envy again which did work

---

