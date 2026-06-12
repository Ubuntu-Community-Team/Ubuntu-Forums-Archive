---
title: "FIX Suspend to RAM Macbook Pro C2D"
date: 2007-05-06
forum: Apple Intel Users
---

### Post by The_Giver on 2007-05-06
So I was having a really tough time with my suspend to ram but I found this guide:


[http://www.andybotting.com/wordpress/?p=176#comments](http://www.andybotting.com/wordpress/?p=176#comments)



In /etc/default/acpi-support,  change POST_VIDEO from true to false. Just restart (I tried logging off and some really nasty stuff happened when I tried to log back in).


EDIT: The cost of having suspend to ram work is that you cant really log off.. and then log back in... oh well I think I would rather have suspend to ram instead... unless someone can find a workout (perhaps a script that updates this accordingly?)

---

