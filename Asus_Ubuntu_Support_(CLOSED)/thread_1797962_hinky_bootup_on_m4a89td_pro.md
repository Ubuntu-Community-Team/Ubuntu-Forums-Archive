---
title: "hinky bootup on m4a89td pro"
date: 2011-07-05
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Ievoigh0 on 2011-07-05
I downloaded and installed 10.10 from CD. System booted fine from the power button and from any key.
I upgraded to 11.04 and now when I cold boot from any key, I have to wait for a blank purple screen, count 5 seconds, press any key and hope it boots correctly. Sometimes it hangs up and I get an orange cursor on a black screen. The only way out of that is to Ctrl-Alt-Del and let it reboot to the OS selector, then it goes to a black screen with a gray cursor and waits for me to press any key.
Is there some sort of MoBo setting I need to change, or maybe a file I can tweak? The system will eventually boot, but this is a hassle.

---

### Post by sanguinoso on 2011-07-05
Did you run the upgrade or did you do a fresh install?

---

### Post by Ievoigh0 on 2011-07-05
Ran upgrade, not fresh install.

---

### Post by sanguinoso on 2011-07-05
Is it a dual boot system?

---

### Post by Ievoigh0 on 2011-07-05
no, only ubuntu 11.04

---

### Post by sanguinoso on 2011-07-05
It might be worth a try to re-install grub. Its sounds like something may have gotten messed up during the upgrade. [https://help.ubuntu.com/community/Grub2#Methods of Reinstalling](https://help.ubuntu.com/community/Grub2#Methods of Reinstalling).

By the by, a lot of people have seen problems when trying to do the upgrade. I believe doing a clean install is the recommended method.

---

### Post by Ievoigh0 on 2011-07-05
Thanks. Haven't tried it yet, but it makes sense, so marked resolved. That complicated and this late int he update cycle, I'll wait until I upgrade my HDD and do a fresh install.

---

### Post by Ievoigh0 on 2011-08-23
UPDATE: The situation seems to have cleared itself as mysteriously as it came. Noticed a new kernel update today. Maybe that solved it.

---

