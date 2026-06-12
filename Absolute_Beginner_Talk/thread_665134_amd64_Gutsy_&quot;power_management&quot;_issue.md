---
title: "amd64 Gutsy &quot;power management&quot; issue"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by Miroku on 2008-01-11
hello -- didnt know where to put this topic, in the beginner forums or the x86 forums, but here goes

so i recently installed gutsy amd64, im not sure whether i notice any performance gains but i did notice that i am not as happy as i was with ubuntu when i was running the 'regular' gutsy. so i probably will be returning to 32 bit computing on the next release, hopefully. getting flash to work has been a little bit more work (yes im lazy), clamAV and AVG refuse to work correctly and these are the things i noticed in the first few days with it.

but aside from my little 64 bit experience, my question is, why cant i access my 'power management' component? i click it, the cursor acts busy and then nothing happens. i dont really need to do anything with it (its a desktop thats always on), its just that when i put on my monitor, it gave me this warning about how "power management cant gather data" .. whatever that means.

can anyone shed some light on this issue? TIA.

---

### Post by nikoPSK on 2008-01-13
Does this run? Give me the output please.

```
gnome-power-preferences
```

~/nikoPSK

---

### Post by ifishfortorque on 2008-01-13
I had this problem too -- it turned out that HAL crashed without protest due to an unrelated network problem (Gnome's network manager chokes on bridge interfaces).  This fixed it for me: 

sudo /etc/init.d/hal restart

This should restart the hardware abstraction layer daemon.  If that doesn't fix the problem, post the output requested above.

---

### Post by nikoPSK on 2008-01-13
> **ifishfortorque said:**
> I had this problem too -- it turned out that HAL crashed without protest due to an unrelated network problem (Gnome's network manager chokes on bridge interfaces).  This fixed it for me: 

sudo /etc/init.d/hal restart

This should restart the hardware abstraction layer daemon.  If that doesn't fix the problem, post the output requested above.

Thank you for that command, helped my friend too. :)

---

### Post by Miroku on 2008-01-15
> **ifishfortorque said:**
> I had this problem too -- it turned out that HAL crashed without protest due to an unrelated network problem (Gnome's network manager chokes on bridge interfaces).  This fixed it for me: 

sudo /etc/init.d/hal restart

This should restart the hardware abstraction layer daemon.  If that doesn't fix the problem, post the output requested above.

awesome! thx for the info.

---

### Post by nikoPSK on 2008-01-15
Please mark this thread as "SOLVED". :)

nikoPSK

---

