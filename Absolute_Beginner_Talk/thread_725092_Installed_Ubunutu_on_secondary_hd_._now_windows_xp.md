---
title: "Installed Ubunutu on secondary hd . now windows xp pro will not boot on main drive"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by deathwish711 on 2008-03-15
Okay i installed xp pro on my main drive as usual . then after getting it setup the way i wanted i saw ubuntu and thought i would give it a go . I installed Ubuntu on my secondary drive so they would each have thier own space . Well now  ubuntu boots fine but  no otion to boot into windows. If i dedicate my first boot device in bios to my main drive and restart  it comes up with ntldr missing . So how can i fix this so that i can  boot into either windows or  ubuntu . I am knew to all this that is why i am here :) please help

ps :  Windows xp pro is on a sata drive and is the main hard drive for this system . Secondary drive and were i have ubuntu installed is an ide hard drive .

---

### Post by bumanie on 2008-03-15
Probably having 'mixed' drives is at least part of the problem. You will probably have to do a 
map (hd0) (hd1) 
map (hd1) (hd0) 
edit in your /boot/grub/menu.lst
Read this link (it's a lot to read). It answers problems such as yours.
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

