---
title: "Putting drive in a different computer"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by belovedmonster on 2008-01-30
If I've got Ubuntu installed on a second drive on my computer can I then put that buntu drive into a different computer (again as the second drive), or will the (second) computer not like that?

---

### Post by dcstar on 2008-01-30
> **belovedmonster said:**
> If I've got Ubuntu installed on a second drive on my computer can I then put that buntu drive into a different computer (again as the second drive), or will the (second) computer not like that?

It may work, but chances are it will not.

When Ubuntu is installed it configures itself to a specific hardware configuration, unless the other PC has exactly the same configuration then things can get (very) confused.

---

### Post by laidback on 2008-01-30
I have done this but as mentioned above the computer hardware needs to be the same or very similar. For me the screen, keyboard and mouse are shared so no problem there. I was lucky in that the graphics worked on either machine. But do make sure that you change the hdd's setting to MASTER (that's done with the jumpers on the back of the drive) as Linux doesn't like cable select and I assume you currently have it set to slave.
I have also tried it between PCs where the hardware was different, i.e. original was using an Athlon 1500 XP on a socket A board whilst the receiving PC was a 939 m/b running Athlon 3500+, it didn't work. For this setup I resorted to a fresh install and then copied over my home directory thus keeping personnal settings in Firefox etc.

---

