---
title: "System configuration problem"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by Alvo on 2006-11-08
Hey guys, noob here.

Got a problem. Decided to give Ubuntu a shot today. Got everything installed, all seems to work fine. As per instructions I deleted the oem user. The first time I restart afterwards, Ubuntu freezes at the splash screen and does nothing. I restart again and it boots and I get the system configuration screen. I get to step 4 where you type in your username/password/etc. and it wont go past step 4. Are there some restrictions to usernames/passwords, or are there certain requirements like a combination of numbers/letters in passwords? 
Any help would be appreciated. Thanks.

---

### Post by bswilson on 2006-11-08
> **Alvo said:**
> As per instructions I deleted the oem user. 

Which instructions are you referring to?  What **exactly** did you do?

---

### Post by Alvo on 2006-11-08
At some point in the installation it told me that after everything is setup, to go into the command line and type in sudo oem-config-prepare. Which is supposed to remove the oem user and automatically launch the system configurator where I can setup my own account

---

### Post by localuser on 2006-11-08
Which version are you installing?

6.06, 6.10?
32-bit, 64-bit?
Desktop, Server, Alternate CD?

Also which instructions are you reading?

---

### Post by Alvo on 2006-11-08
Sorry guys, shoulda thought about that.

I'm running 6.10 Alternate CD x64
____________________________________________

I fixed it. Just reinstalled in text mode, that bypasses the whole OEM user thing. 

Thanks for the help though.
Friendly community you guys have here. :D

---

