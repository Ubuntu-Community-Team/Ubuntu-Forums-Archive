---
title: "Dual Boot install order?"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by anim on 2007-05-25
Hello, not quite an absolute beginner, but figured this was the appropriate place for this question.

I am in the process of building a new system and for the first time I wont have factory installed XP on a system I own. I am planning on installing XP professional and Fiesty Fawn on the new system, and I was wondering if anyone would recommend installing one OS before the other. I do know windows can be somewhat disagreeable for random reasons so I hope this question has some merit.

I have one 500GB SATA HD, no raid so I'm not trying to split the OS's or anything fancy.

---

### Post by drowner on 2007-05-25
From what i have gleaned (i dont use vista) XP plays nicer with linux than vista.

But windows does not play nice.

The question has merit: install windows first, then ubuntu

during the ubuntu installation a program called 'grub' will be installed to your master boot record, it will detect windows and give you the option of which to boot.

If you install windows after ubuntu, windows will overwrite the MBR and then it wont let you access ubuntu, it can be fixed later, but its one extra hassle you can avoid.

Hope that helps.

---

### Post by oilchangeguy on 2007-05-25
windows first, then ubuntu.

---

### Post by anim on 2007-05-25
Thank you.

---

