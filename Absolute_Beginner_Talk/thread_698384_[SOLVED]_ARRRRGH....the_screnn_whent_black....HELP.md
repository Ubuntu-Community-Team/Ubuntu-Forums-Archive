---
title: "[SOLVED] ARRRRGH....the screnn whent black....HELP!"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by Nick8692 on 2008-02-16
last night, i think i turned off power management in sessions by accident :(

When i select Ubuntu in grub,  the login sound effect plays, but the screen in BLACK...
Then i log in enter my login details, press enter...and it plays the sound it plays when i log in, but the screen is still black.....

I have no experience of recovery mode, so can someone please help me?

:confused::confused::confused:

---

### Post by mikeyphi on 2008-02-16
Boot into recovery - it's just a bunch of text before settling at the command prompt!

Enter "dpkg-reconfigure xserver-xorg" without the quotes
there will be several pages of text with a question at then of each section - accept the default answer unless you know different!
After rebooting you should have the screen back but will probably need to set up resolution etc.

---

### Post by zerhacke on 2008-02-16
You'll need to put sudo in front of that dpkg command.

---

### Post by mikeyphi on 2008-02-16
> **zerhacke said:**
> You'll need to put sudo in front of that dpkg command.

Recovery mode on my Gutsy system fires up as root....so sudo is not required

---

### Post by nikoPSK on 2008-02-16
could you try reconfiguring xorg please?
```

sudo dpkg-reconfigure --phigh xserver-xorg
```

That should work for your issue. :)

--phigh puts settings at optimum.

---

### Post by Nick8692 on 2008-02-16
thanks guys, my screen is working again :)

---

### Post by nikoPSK on 2008-02-16
> **Nick8692 said:**
> thanks guys, my screen is working again :)

No problem, please mark this thread as "SOLVED" by going to the Thread tools menu at the top of the thread. :)

---

