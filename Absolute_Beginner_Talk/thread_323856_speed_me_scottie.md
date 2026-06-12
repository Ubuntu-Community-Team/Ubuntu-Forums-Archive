---
title: "speed me scottie"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by abu-fatu on 2006-12-22
i'll try it again i am dual booting edgy and xp .using dsl on firefox (xp) swiftfox,firefox,opera (edgy) in xp my dsl is dsl!! while on edgy it runs more like dial up . please tell me what can i do? to speed it up.

---

### Post by Atomic Dog on 2006-12-23
Try searching the forum for disable ipv6.  I bet $100 that this will solve your problem.  Make sure you grep for ipv6 after you make your changes to be sure ipv6 is totally removed.

---

### Post by slimdog360 on 2006-12-23
yep, its always the ipv6 thing. I was for mine and this is how I fixed it.

```
sudo nano /etc/modprobe.d/aliases
```
find this line in the file: 'alias net-pf-10 ipv6'
chage it to this: 'alias net-pf-10 off'
save the change and reboot

I got that from the mepis forums.

---

### Post by Atomic Dog on 2006-12-23
...and also disable it in firefox by typing "about:config" as the address.  Set network.dns.disableIPv6 to true...for good measure.

---

### Post by jbutler12 on 2006-12-23
Do you have BellSouth DSL?  If not, this doesnt apply.  But BellSouth has something stupid called "FastAccess" that runs in the background on windows and does some authentication (you can buy different DSL bandwidth levels from bellsouth) and i think that controls it... since LInux doesnt show it, i think it thinks you are on the slowest level.  A simple change in your DNS settings can fix this, but let me know if you are on BellSouth so i dont waste time posting it all up.

---

