---
title: "Upgrade to 7.10 crashed Display"
date: 2007-12-19
forum: Apple PPC Users
---

### Post by ebioman on 2007-12-19
Hi,
 I had very long time good running feisty and upgraded now to gutsy - bad mistake.
 I got multiple problems like the ide_core stuff and slow performance...
 Most of them I could fix, but there is still one unsolvable:

 I ve got a
 Powerbook Titanium with 400MHz and a 
 normal display resolution with 1152x768 and 31-46 vert. 50-70 hor. Hz.

 With Feisty I just wrote it in the xorg.conf and used the r128 driver for the ati mobility graphic chip. But this is not possbile anymore. If I write just in the xorg.conf I get a lot of stripes and strange video behavior. 

I tried dpkg-reconfigure -phigh xserver-xorg. With that I get a strange xorg.conf that don t work either, but this new rescue system for the xserver can finally show me a gnome-desktop. But when I want to change display resolution I can t select 1152X768 even if its in the xorg.conf :confused:


Normaly I would just take again the feisty and make a new installation because gutsy for ppc is complet **** but my optical CD-Drive crashed and I can t do a new installation......

---

### Post by stmiller on 2007-12-20
Can you copy and paste your /etc/X11/xorg.conf file here? And also did you check the /var/log/Xorg.0.log for errors?

---

### Post by ebioman on 2007-12-22
Thanks for the answer, 
but at the moment I don't have the laptop with me, but
I'll check it next week

---

### Post by ebioman on 2008-01-04
Hi here my files:

xorg.conf:

[http://ubuntuusers.de/paste/26694/](http://ubuntuusers.de/paste/26694/)

var/log/Xorg.o.log:

[http://ubuntuusers.de/paste/26692/](http://ubuntuusers.de/paste/26692/)

Whats very strange, that it's working with the rescue service when I use the 
given values for hor. and vert. range that fit definitely not for my display. If I change them to the correct values everything crashes :(

---

