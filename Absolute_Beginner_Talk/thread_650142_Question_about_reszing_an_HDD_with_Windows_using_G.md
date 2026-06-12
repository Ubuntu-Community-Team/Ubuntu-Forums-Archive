---
title: "Question about reszing an HDD with Windows using GParted"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by Jaimes_Phazon on 2007-12-25
Can I use gparted to resize my hardrive that has Windows on it and is about 85% full without losing  any data?

---

### Post by adam.tropics on 2007-12-25
Well yes, but be careful. I have had mixed success...mostly positive though. As with anything else backup data first, and have a plan ready if it all goes wrong!

Normally, it will resize fine, then when you boot windows, it will smell a rat and do a full file system check, which seems to just allow it to see the new space it's just been given, then after that , all good.

---

### Post by Jaimes_Phazon on 2007-12-26
Okay thanks. I just wasn't sure about it because I thought if all my files are spread out on the disk I thought it would just write over some of them maybe and not the free space.

---

### Post by LaRoza on 2007-12-26
> **Jaimes_Phazon said:**
> Okay thanks. I just wasn't sure about it because I thought if all my files are spread out on the disk I thought it would just write over some of them maybe and not the free space.

Defrag first if that is the case, also, back anything up you can't afford to lose. I never had trouble with GParted and data integrity, but you never know.

It will move the files if they are in the way.

---

