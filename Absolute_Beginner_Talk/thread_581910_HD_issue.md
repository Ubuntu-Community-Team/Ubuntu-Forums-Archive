---
title: "HD issue"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by BlueNosE on 2007-10-19
hey,
i have system crushes, and now i just found why.

the hard disk makes crushes while installing, playing, etc.

now, if i will install ubuntu on another HD without the first HD connected, grub will identify the first HD after installing it on the second one? (i mean, 1. unplug the first HD with windows XP, 2. install ubuntu on second HD, 3. plug the first HD with windows XP to make dual boot)

---

### Post by 1337455 10534 on 2007-10-19
Are you basically saying a double HDD boot choice worked? Worth looking into... Post how you did it.

---

### Post by BlueNosE on 2007-10-19
i didnt understand ur question,
maybe because u didnt understand me.

i have  hard disk called X and hard disk called Y. hard disk X has windows XP. 
i want to unplug hard disk X and install linux on hard disk Y, and then plug hard disk X again as slave os.

would it work?

---

### Post by BlueNosE on 2007-10-19
i didnt understand ur question,
maybe because u didnt understand me.

i have hard disk called X and hard disk called Y. hard disk X has windows XP.
i want to unplug hard disk X and install linux on hard disk Y, and then plug hard disk X again as slave os.

would it work?

---

### Post by oilchangeguy on 2007-10-19
> **BlueNosE said:**
> i didnt understand ur question,
maybe because u didnt understand me.

i have hard disk called X and hard disk called Y. hard disk X has windows XP.
i want to unplug hard disk X and install linux on hard disk Y, and then plug hard disk X again as slave os.

would it work?

should work ok. but in here there are many people whose first language is not english. so if you want to be understood. actually spell words. ur and u are not words.

---

### Post by logos34 on 2007-10-19
> **BlueNosE said:**
> i have hard disk called X and hard disk called Y. hard disk X has windows XP.
i want to unplug hard disk X and install linux on hard disk Y, and then plug hard disk X again as slave os.

would it work?

Should work.  After install make sure Y drive is set first in the BIOS hard disk boot priority.  To boot XP either switch the boot order in the bios or add a [windows entry]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk") to the bottom of /boot/grub/menu.lst with appropriate drive mapping lines (to effect a '[virtual swap']("http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows")).

---

### Post by BlueNosE on 2007-10-19
> **oilchangeguy said:**
> should work ok. but in here there are many people whose first language is not english. so if you want to be understood. actually spell words. ur and u are not words.

Well, you right. I'm sorry.

Thank you. I'll try now.

---

### Post by BlueNosE on 2007-10-19
I can't understand something.

[http://img484.imageshack.us/img484/2952/screenshot1jm8.png](http://img484.imageshack.us/img484/2952/screenshot1jm8.png)

The hard disk already has parts - why should I format the whole HD? Can't I just format a small part?

Earlier today, I tried to install and entered to the partition part, and I had an option to change the partition size on my own. It just disappeared. (?)

---

### Post by logos34 on 2007-10-20
have you tried the 'manual' partitoning option?

---

