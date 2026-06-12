---
title: "Couple Of Questions"
date: 2005-07-08
forum: Absolute Beginner Talk
---

### Post by piedrin on 2005-07-08
First of, let me start by saying that Ubuntu is a great distro and it works great, but I need help with a couple of things.
Right now Ubuntu is running on an HP Pavilion ZE4315us laptop and when it boots up, I see a message about ATI IGP Northbridge not yet fully tested.
Should I be worried about this?
Also I've noticed that Laptop battery is not as long as when I was running XP on
the same laptop.                                                                                                     Since installing Ubuntu I wiped out windows completely. YEEEAAAAHHHHHHH!!!!

I would appreciate it if you all linux users with more experience could help me out.
                                                   

                                                                                                     Thanks!!!

---

### Post by Kvark on 2005-07-08
[QUOTE=piedrin]First of, let me start by saying that Ubuntu is a great distro and it works great, but I need help with a couple of things.
Right now Ubuntu is running on an HP Pavilion ZE4315us laptop and when it boots up, I see a message about ATI IGP Northbridge not yet fully tested.
Should I be worried about this?
Also I've noticed that Laptop battery is not as long as when I was running XP on
the same laptop.                                                                                                     Since installing Ubuntu I wiped out windows completely. YEEEAAAAHHHHHHH!!!!

I would appreciate it if you all linux users with more experience could help me out.
                                                   

                                                                                                     Thanks!!![/QUOTE]

For ATI cards you need the packages with "fglrx" in their name and one of the restricted modules that mention "fglrx" in their description.

The battery issue can be caused either by ubuntu giving cpu and other components less idle time then xp gives, in this case anything that reduces workload on the computer helps. Or by xp drivers being smarter when it comes to temprature monitoring and fan control, dunno what to do in this case, finding smarter drivers or tweaking fan control may be hard.

---

