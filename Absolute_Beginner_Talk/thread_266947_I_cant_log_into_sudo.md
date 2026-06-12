---
title: "I cant log into sudo"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by Cran1988 on 2006-09-28
Hi i have big problem i can t log into sudo but i can log into my name!
U see i was making a second user but i dont know how i put the same restriction to my original name!And that the problem now i cant install or open some media even if i go with my original name or my original password!

Is like that i lock myself!!!!

plz help me what can i do? :-k ](*,) 


(sry for my bad english i m greek)

---

### Post by jISh on 2006-09-28
Go into your recovery mode (in the GRUB menu at startup) and then at the root prompt type:
```
gpasswd -a yourname admin
```
Should have access to sudo after that.

---

