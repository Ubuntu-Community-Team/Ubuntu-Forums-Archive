---
title: "Computer won't wake from sleep"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by SlaughterDog on 2007-05-08
This is a problem I've noticed since I started using Ubuntu. When the computer goes to sleep/standby/suspend, it doesn't wake up. However, when I use Windows, it does wake up. With Ubuntu, the screen just stays black, and sometimes the HDD light and VGA fan stay on and at max. I don't know if this is a BIOS problem or a Ubuntu problem, but seeing as Windows will wake up, I'm thinking it's a BIOS problem. My mobo is an Asus P5B and I *did* update my BIOS to the latest version.

---

### Post by lich 6222 on 2007-05-08
> **SlaughterDog said:**
> This is a problem I've noticed since I started using Ubuntu. When the computer goes to sleep/standby/suspend, it doesn't wake up. However, when I use Windows, it does wake up. With Ubuntu, the screen just stays black, and sometimes the HDD light and VGA fan stay on and at max. I don't know if this is a BIOS problem or a Ubuntu problem, but seeing as Windows will wake up, I'm thinking it's a BIOS problem. My mobo is an Asus P5B and I *did* update my BIOS to the latest version.

did you chek your Bios ?
pressing DEL at start up

eli

---

### Post by SlaughterDog on 2007-05-08
> **lich 6222 said:**
> did you chek your Bios ?
pressing DEL at start up

eli

Check it for what? I toyed with setting things like advanced power tables (whatever those are), no dice.

---

### Post by SlaughterDog on 2007-06-04
Well it still won't work; wakes from Windows but not Ubuntu.

---

### Post by SlaughterDog on 2007-06-21
So I found out a bit more, if anyone actually reads this and had the same problem, hopefully this will help.

It looks to me like it's up to hardware drivers to reprogram a lot of hardware when you try to resume. Video card drivers usually don't do this right. I have an ATI card, and I noticed that in kernel patch 15, it has restricted drivers, but in 16, it doesn't. 16 had problems with video lag from that but it *does* suspend and resume successfully. 15 doesn't and I'm assuming that's because of the restricted propriatary drivers.

---

