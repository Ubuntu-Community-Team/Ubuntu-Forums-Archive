---
title: "Live Cd and LAternate cd wont work"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by redeyeskyo on 2007-07-14
I have been geting excellent help form here and would like to thank everyone. BUt I have checked the hases bruned in the right speed and I can not get ubuntu to run/install on my pc. All they do is go to a black screen . I really want to swtich from xp. Can someone out there help me. I even tried to partion my drive but it i couldnt even gt my pc to do that. Please someone help ?

---

### Post by BobCFC on 2007-07-14
Try to get a specific error message to chew on. If you press F6 to edit the boot options on the menu and change **spash** to **nosplash** this will skip the logo.  If you remove **quiet** this will give more detailed errors.

Sometimes this will get you to an emergency prompt where you can review the log with 

more /var/log/casper.log

---

### Post by shearn89 on 2007-07-14
How old is your computer? I had problems on my laptop, as it didn't like to boot from burnt cds... Can you get to the ubuntu install menu - the very first one (install/run ubuntu, check cd, etc..)?

---

