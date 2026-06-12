---
title: "missing stuff in the menu of a fresh install"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by benner on 2007-07-11
i just did a fresh install of ubuntu (dual boot) and everything seemed to go fine.  but when i looked at the system > administration menue there were only 5 or 6 items.  for example, 'shared folders' wasn't there.  ever seen this happen?  suggestions?  thanks in advance....

---

### Post by corney91 on 2007-07-11
You should be able to edit menus using alacarte:

```
sudo alacarte
```

This should allow you to bring back the menu options.

---

### Post by benner on 2007-07-11
didn't work.  nothing opened.  when i right click on the menus at the top and select 'edit menus' everything comes up.  but when i try to add a checkmark to the boxes to add items, after about a second, there is a click sound and the checkmark disappears.  weird.

---

### Post by benner on 2007-07-11
i think for some reason i am not an administrator on the system.  but there is only 1 user on the machine.  me.  i just installed it an hour ago.  when i tried to use the update manager it gave me an error i didn't understand and told me to contact my system administrator.  how can i get in as an admin (if that is the problem) so i can change it?

---

### Post by benner on 2007-07-11
i was right.  for some reason the instal didn't give me admin rights.  i rebooted into recovery mode and did addgroup "username' admin and everything worked.

---

### Post by pyros on 2007-07-11
> **benner said:**
> i was right.  for some reason the instal didn't give me admin rights.  i rebooted into recovery mode and did addgroup "username' admin and everything worked.

That's really strange, I wonder why you weren't added by default.

---

### Post by americanmetal07 on 2007-07-25
> **benner said:**
> i was right.  for some reason the instal didn't give me admin rights.  i rebooted into recovery mode and did addgroup "username' admin and everything worked.


For some reason it just did that to me to. 
I'll do what you did to fix it.

---

### Post by pyros on 2007-07-26
Would you both mind posting what version of ubuntu you installed and whether you used the desktop or alternate install cds?

---

