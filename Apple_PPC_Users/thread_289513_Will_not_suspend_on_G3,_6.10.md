---
title: "Will not suspend on G3, 6.10"
date: 2006-10-31
forum: Apple PPC Users
---

### Post by Mazmot on 2006-10-31
I have some problems since I upgraded from 6.06 to 6.10. Particularly I am troubled on power manager. When I try to make my iBook(500MHz G3) suspended with the lid closed or select from menu, it never sleeps. Actually, it will be turned off, but as soon as the light goes out, it will switched on again. 

I used 6.06 for four months, and the power manager worked fine. It warned me that the suspending is somewhat buggy, but nonetheless it worked. This time, there is no warning, but it doesn't work. I tried Kpowersave, but it seems that it depends on the same information and will not let the iBook suspended. 

Is this problem unique to me, or is there someone else who suffers on the same trouble?

---

### Post by cmorgan47 on 2006-10-31
same laptop, works fine.
if you try to suspend it manually--ie with the "power off" button, or power manager icon--does it work then?

---

### Post by Mazmot on 2006-10-31
> **cmorgan47 said:**
> same laptop, works fine.
if you try to suspend it manually--ie with the "power off" button, or power manager icon--does it work then?

Thank you for your advice. I've tried, but it is all the same. Go to sleep, then in a moment, it wakes up. Usually when iBook goes to sleep, the small LED near the lid button blinks. Instead, the display starts. Now I don't know what can I do.

---

### Post by cmorgan47 on 2006-10-31
outside of clearing out your log file, trying to suspend it, then checking the messages, no advice.... /var/log/acpid i think...don't have one here.

---

### Post by Mazmot on 2006-11-03
I found one not-so-smart way to suspend my iBook. First, go to the exit menu and click to change user. Current session should be stored in ram. Then, at log-in dialog, select suspend in the option menu. Then, my system goes to sleep. It takes too much time and make it less useful. 

My guess is, that my problem is in the desktop program, for without nautilus running, I can make it suspended well. One step forward, but still lost.

I am in a Japanese environment, and the some words may be wrong. There always be problems in translating back. And some of my log are described in Japanese. Sometimes it makes me hard to get a proper advise.

---

### Post by Mazmot on 2006-11-06
My problem has all been solved after I re-installed 6.10 from live CD. It must have been something left from 6.06 which caused a lot of trouble. Very basic lesson I learned: If you get lost, stat all over. 

Thanks everybody!

PS; I found along the way that 6.10 has far better Japanese environment compared to 6.06. This is a good news for Japanese users like me.

---

