---
title: "Can't update, error message"
date: 2010-11-08
forum: Any Other OS
---

### Post by myolbug on 2010-11-08
Mint 9 64 Bit. I hit Alt F2 and typed in upgrade.  Something flashed in a terminal too quickly to read.  Now, when I go to run updates, this message appears;
[I]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/I]

Ideas?  I ran the configure -a, but nothing happens.

---

### Post by plucky on 2010-11-08
> **myolbug said:**
> Mint 9 64 Bit. I hit Alt F2 and typed in upgrade.  Something flashed in a terminal too quickly to read.  Now, when I go to run updates, this message appears;
[I]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/I]

Ideas?  I ran the configure -a, but nothing happens.

Open a terminal and ```
sudo apt-get update && sudo apt-get upgrade
``` and post any output if there are any errors.

Enclose it in [noparse]```

```[/noparse] blocks.

> I hit Alt F2 and typed in upgrade.

What are you expectations for that command?

---

### Post by Rubi1200 on 2010-11-08
I would do this:

Go to Applications > Accessories > Terminal

Then run the command ```
sudo dpkg --configure -a
```

Report back if there are errors.

If not, run the command suggested above by plucky.

---

### Post by myolbug on 2010-11-09
Hey all, this all boils down to the fact that me working 60 hours a week and a tired me, combined with a terminal is a bad combo.  Both of your suggestions worked.  I realized tonight that the reason *tsudo dpkg --configure -a *wasn't working is that when I did a cut and paste of the command, I had accidentally included ' in it.

I did the above, then your suggestion plucky and all is well!

---

### Post by Rubi1200 on 2010-11-10
Excellent! Glad you got things sorted out :)

---

