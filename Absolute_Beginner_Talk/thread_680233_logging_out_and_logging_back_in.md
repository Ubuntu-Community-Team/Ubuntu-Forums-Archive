---
title: "logging out and logging back in"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by sirzepp on 2008-01-27
When I log into my computer after logging out, I get nothing but a mouse pointer and a tan colored desktop.  No panels, no icons, no desktop background.  Desktop Effects are disabled and I'm using the latest nvidia driver.

When I CTRL-ALT-Backspace to the GDM logon, I can restart.  When I restart, I can log into my desktop just fine, but once I logout, I have to restart to log back in.

I've used ENVY to install my nvidia driver...

I've solved this before, I just can't remember how.

---

### Post by Majorix on 2008-01-27
The answer is simple: You shouldn't have used Envy. That tool is buggy and may make your computer unusable. So if you can't run it to uninstall the drivers it installed (which I believe you can't) then you are forced to do a format.

Sorry mate.

---

### Post by philinux on 2008-01-27
I thought envy was quite well respected?

---

### Post by Joeb454 on 2008-01-27
**Majorix** I can't have you saying that :) I've used Envy before on my Desktop PC, and I'll admit that I did have issues upgrading from 7.04 to 7.10

However from what I recall, Envy does let you uninstall drivers, though I'm not sure how good it is at doing so.

Either way, it's not horrible software *cough**automatix**cough* but as of Gutsy (7.10) there is less need for using Envy

---

### Post by Majorix on 2008-01-27
> I thought envy was quite well respected?
Well maybe it is, but on my side it only produced problems. I used it twice but won't go for it for a third one.

---

### Post by sirzepp on 2008-01-27
While I appreciate all the help here...the simple answer is not always true.

I used ENVY because of this problem.  I've had this problem since installing Gutsy for the fifth time this week and at one point I had all my video working well(on an earlier install)...but I can't remember what I did(I did not use envy that time).  So, ENVY is not the issue...there is something that I've done in the past to fix this and I can't remember what I did.  This problem existed on my machine before envy:).

Thanks, though.

Some other help would be nice.

---

### Post by Joeb454 on 2008-01-27
Well it's definitely a graphics related problem.

When you're logged in could you check the Restricted Drivers. Somewhere under System>Administration I believe

---

### Post by sirzepp on 2008-01-27
I don't have any menus or anything...just a tan desktop with a mouse(no panels are loaded).

Envy is uninstalled...I'll try automatix.

---

### Post by sirzepp on 2008-01-27
Automatix doesn't have an nvidia driver option on my machine...seems like I saw that there before...but not now...

---

### Post by Joeb454 on 2008-01-27
I didn't mean automatix.

You said if you restart that you can use the PC normally?

---

### Post by sirzepp on 2008-01-27
Alright, I disabled nvidia and went back to the "nv" driver.  I can log out and in to my heart's content.  However, I'd like to run the nvidia driver.  Any help?  I swear, I had this all working a few days ago WITH compiz and emerald running.  It was awesome.  I broke something else(learning curve, right?) and had to re-install.  Now I can't figure out what I did to fix things.

---

### Post by sirzepp on 2008-01-27
> **Joeb454 said:**
> I didn't mean automatix.

You said if you restart that you can use the PC normally?


That's correct.  With the nvidia driver enabled(and even with NO effects turned on).  I can restart, log in, and compute all day!  When I log out, I cannot log back in...I just get the "TSOAD"(Tan Screen of Almost Death...almost because I still have a mouse pointer at least!).

---

### Post by Joeb454 on 2008-01-27
Hmmm...well it sounds like you've tried enabling the Nvidia Drivers from the restricted drivers manager.

I'm stumped now...partly because it's 1.30am, but at least we know you can use the 'nv' driver until it's sorted

---

### Post by sirzepp on 2008-01-27
> **Joeb454 said:**
> Hmmm...well it sounds like you've tried enabling the Nvidia Drivers from the restricted drivers manager.

I'm stumped now...partly because it's 1.30am, but at least we know you can use the 'nv' driver until it's sorted

Yeah, that is true!  Funny how the open-source driver works so well, eh?  I know it's not 3-d, but it does seem reliable.  I'll keep tinkering.  I've removed all nvidia stuff and I'm going to retry the restricted drivers.

---

### Post by Joeb454 on 2008-01-28
Let us know how it goes :)

---

