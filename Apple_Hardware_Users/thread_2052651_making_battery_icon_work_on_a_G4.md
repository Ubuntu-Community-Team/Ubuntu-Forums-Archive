---
title: "making battery icon work on a G4"
date: 2012-09-03
forum: Apple Hardware Users
---

### Post by 2blue on 2012-09-03
I have a managed to get a battery/adaptor icon on the lower right taskbar, but it does not work. I have followed the guide on the ppc faq page but I can not make it show charge ( how full or empty the battery is).  I have  just bought a new aftermarked battery which luckily works fine.  

What I have done is paste "gksudo gedit /etc/modules", I have to fill in password, and then I paste in "pmu_battery",  but it says "command not found".  There is a remark about leafpad, but I don`t understand how it is relevant. 

Any idea on how to go about it?

Edit: adaptor shows as "online" at all times which I intepret as #plugged into the wall", a bit confusing with wireless adaptor, bit this is the xfce power-manager.

---

### Post by 2blue on 2012-09-04
I have searched through what I could find on lxde power-manager. Some  get the battery charge indicator to show when hoovering cursor above the icon (on taskbar). I suppose there are too few using lubuntu and lxde to post. 

I have discovered there is quite a large after marked for replacement parts for older powerpcs, like batteries and chargers, must be quite a lot who still use them.

---

### Post by rsavage on 2012-09-04
For lubuntu you replace gedit with leafpad as per instructions.
 
gksudo leafpad /etc/modules

---

### Post by 2blue on 2012-09-04
I was a bit slow there rsavage, I didn`t understand the part about leafpad, but when I did it right it is of course obvious :redface: Battery indicator now all working !! 

Thanks :- )

---

### Post by 2blue on 2012-09-05
I have been charging battery for ages, and indicator shows "Adaptor is online. Your battery is fully charged 46%".  Which is on the weird side as it should show 100% and my adaptor is not plugged in. ??!! In other words, computer is running on battery.

---

### Post by 2blue on 2012-09-09
I`m tempting to "unsolve" this tread again. Battery indicator works in part, but it needs a full reboot to sort of take info on the current state battery. When I plug in the charger powermanager reacts and show the increasing levels, but on discharge it is stuck on what ever level it was when unplugged. It shows "fully charged 99%" still when computer goes in dormant mode due to flat battery. 

!!??

---

### Post by standarshy on 2012-09-10
I've noticed that, althought still not completely function, the battery icon works a bit better using the gnome interface.  I know that's not really a solution, but, if the interface doesn't bother you, you can try that.

I'm glad this old mac has a battery indicator on the battery itself.  If I'm getting worried, I can just check it.

---

### Post by 2blue on 2012-09-10
Yeah, nice with the battery green lights. Luckily the replacement battery I got have the same feature. I wonder why the indicator doesn`t show properly?

---

