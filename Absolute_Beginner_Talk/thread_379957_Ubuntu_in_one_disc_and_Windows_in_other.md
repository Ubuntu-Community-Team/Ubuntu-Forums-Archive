---
title: "Ubuntu in one disc and Windows in other??"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by piogil on 2007-03-09
I have installed Ubuntu in a new disc (IDE) and set it master and left Windows in the other disc (SATA). How could i choose the  O.S. before Ubuntu start???

Thank you in advance

Salud
Pio

---

### Post by Famicommie on 2007-03-09
Before Ubuntu begins to load, you should be presented with the GRUB menu which will allow you to select the OS you want to boot into. GRUB will automatically boot into Ubuntu after ten seconds, unless you change the default.

---

### Post by piogil on 2007-03-09
I don´t see that Grub menu at start.....

In a spanish forum i´ve read that Grub do not work when Ubuntu and Windows are in separate disc... but it seem very strange to me.....

How could i fix this????

Thank again

---

### Post by Ek0nomik on 2007-03-09
Did you install Ubuntu and than Windows?

Windows may have b0rked your MBR.

---

### Post by piogil on 2007-03-09
Thank for your replie Ekonomik.
No, Windows was instaled in the first disc then i installed a second disc and Ubuntu in it ....

---

### Post by igknighted on 2007-03-09
which HD is your bios trying to boot from?  Try both, grub must be on one of them

---

### Post by Ek0nomik on 2007-03-09
You installed Ubuntu and Windows on separate hard drives than I take it?

---

### Post by adza on 2007-03-09
this is the same as my config.. easy to sort out..I have IDE (secondary) drive with linux and SATA primary with winblows (waiting for the day to BURN!! - nevermind)...
 
Open the BIOS window on re-boot, change the boot priority of your HDD to boot from the IDE (linux) drive first. On my install (6.06) the GRUB boot loader simply detected the previously installed windows on the SATA partition, it includes it in the boot list for you to choose from. This method does depend on windows being installed first however (don't know why though...)

---

### Post by piogil on 2007-03-09
Thankyou guys for your tips and help.... Right now i´m at work, this evenning at home, i will try your advices.

My situation is exactly the one "adza" explain....

Thankyou again

Salud 
Pio

---

### Post by adza on 2007-03-12
Did this fix your issue?

---

### Post by piogil on 2007-03-12
Yes man, everything go perfect following your tips.....

Thnak a lot

Pio

---

### Post by adza on 2007-03-14
well i'm glad i could help :) that's my first 'give' some good solutions, rather than 'receiving' all the time.... **rosy glow** hehe

---

