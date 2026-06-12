---
title: "display problem with sony vaio sz series"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by moiz11077 on 2008-02-15
I m currently running Ubuntu in sony vaio SZ laptop 
i m having problem using display driver of intel chipset 945, it is working in nvidia good but when i switch mode to intel its unable to load Ubuntu and my webcam and fingeprint sensor is not working please help

regards
Moiz

---

### Post by djbsteart1 on 2008-02-15
intel and nvidia? im missing something here please explain. are you using to graphics controllers at once?

---

### Post by jan quark on 2008-02-15
please run

```
 lspci
```

ti see what card you really have nvidia or interl

then you have to install the correct drivers

---

### Post by ceti331 on 2008-02-28
I think the problem he has is that this laptop can change graphics hardware via a swtich for STAMINA (longer batery life) or SPEED (higher graphics performance) ?

As I'm considering purchasing this particular laptop myself, I'd be curious to see any info on this issue.. 

Does ubuntu "configure itself" on installation to work with the graphics card it sees first ?

---

### Post by uberlube on 2008-02-28
I dont see the point in that feature. If you want to use less battery power, turning down the brightness and a couple of other things should be good enough.

---

