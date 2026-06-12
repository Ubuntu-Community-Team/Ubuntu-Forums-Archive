---
title: "help plz with my x server problem and installation"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by Korea91 on 2007-07-05
Help plz on all stuff i need help plz it deals with the installation of ubuntu 

--------------------------------------------------------------------------------

ok im trying to install ubuntu 7.04 the desktop version on my sony vaio VGC-VA11G desktop
ATI MOBILITY RADEON X700
yet when i put cd in and reboot and say install it trys and then goes blank
when i do the safe grafics mode it says x server is wrong and so i tried the sudo dpkg-reconfigure xserver-xorg
but i was so confused with it i didnt no wat to do 
wats wrong with my computer ahhh
it would be very much abliged for any help i really wanna try ubuntu oh and my operating system now is media center XP

---

### Post by John.Michael.Kane on 2007-08-03
Retry using this boot parameter (make sure to hit F6 first add the below command to the boot line, and then try installing).

```
nosplash noapic nolapic
```

---

