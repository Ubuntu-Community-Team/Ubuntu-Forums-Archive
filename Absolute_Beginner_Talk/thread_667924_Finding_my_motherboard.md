---
title: "Finding my motherboard"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by nikoPSK on 2008-01-14
Well, I want some new RAM, but am too lazy to take m rig apart right now to find out what type I need. I have forgotten. I just need to find out what type of motherboard I have to find the RAM.

nikoPSK

---

### Post by Casual Fan on 2008-01-14
I know what you mean. I have to pee, but, whatever.

---

### Post by p_quarles on 2008-01-14
> **nikoPSK said:**
> Well, I want some new RAM, but am too lazy to take m rig apart right now to find out what type I need. I have forgotten. I just need to find out what type of motherboard I have to find the RAM.

nikoPSK
Try a dowsing rod?

Seriously:
```
sudo lshw
```

---

### Post by nikoPSK on 2008-01-14
> **p_quarles said:**
> Try a dowsing rod?

Seriously:
```
sudo lshw
```

I got this:

 *-core
       description: Motherboard
       product: 8IR
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: 1.x
       slot: PCI
:confused:

> **Casual Fan said:**
> I know what you mean. I have to pee, but, whatever.

okay... don't post unless you can help... :shock:

---

### Post by p_quarles on 2008-01-14
> **nikoPSK said:**
> I got this:

 *-core
       description: Motherboard
       product: 8IR
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: 1.x
       slot: PCI
:confused:
So, look up Gigabyte Tech's 8IR mobo. That doesn't even require a screwdriver. ;)

---

### Post by nikoPSK on 2008-01-14
> **p_quarles said:**
> So, look up Gigabyte Tech's 8IR mobo. That doesn't even require a screwdriver. ;)

thank you very much... would it list my ram type too? The command?

---

### Post by p_quarles on 2008-01-14
The "lshw" command doesn't give you enough info about your RAM to know what kind to buy. But, Googling your motherboard will.

---

### Post by nikoPSK on 2008-01-14
> **p_quarles said:**
> The "lshw" command doesn't give you enough info about your RAM to know what kind to buy. But, Googling your motherboard will.

got this:

Supported RAM Technology: DDR SDRAM

---

### Post by meindian523 on 2008-01-14
Does that mean DDR1 SDRAM?

---

### Post by p_quarles on 2008-01-14
> **nikoPSK said:**
> got this:

Supported RAM Technology: DDR SDRAM
Methinks you are not using Google to its fullest potential. ;)

You will also need to select either PC1600 or PC2100 type RAM sticks. 

That's according to my search on that mobo, though. There's no substitute for just opening the case and reading the info on the current stick. Yes, it requires some effort, but it will save you more.

---

### Post by crjackson on 2008-01-14
> **nikoPSK said:**
> got this:

Supported RAM Technology: DDR SDRAM

Go to [http://www.crucial.com](http://www.crucial.com) and use the motherboard wizard.  It will tell you EXACTLY what type of RAM you board uses and other useful information too...

---

### Post by nikoPSK on 2008-01-14
> **crjackson said:**
> Go to [http://www.crucial.com](http://www.crucial.com) and use the motherboard wizard.  It will tell you EXACTLY what type of RAM you board uses and other useful information too...

Thank you very much. Going there now. :D

nikoPSK

---

### Post by nikoPSK on 2008-01-14
Well, SO far, I got, Gigabye->Motherboards... then I can't find my model... :confused:

---

### Post by crjackson on 2008-01-14
I just looked it up for you.  You need PC2100 DDR.

[http://www.memoryx.net/gamo15.html](http://www.memoryx.net/gamo15.html)

---

### Post by p_quarles on 2008-01-14
[http://www.ciao.de/Gigabyte_GA_8IR2003__1267245](http://www.ciao.de/Gigabyte_GA_8IR2003__1267245)

---

### Post by nikoPSK on 2008-01-14
> **p_quarles said:**
> [http://www.ciao.de/Gigabyte_GA_8IR2003__1267245](http://www.ciao.de/Gigabyte_GA_8IR2003__1267245)

I got there... :) Now what about recommended memory close to BC, canada?

---

### Post by p_quarles on 2008-01-14
> **nikoPSK said:**
> I got there... :) Now what about recommended memory close to BC, canada?
Given the size of the province of British Columbia (beautiful place, btw), I'd have to that "close to" it could include everything from Taipei to Reykjavik. You wanna be more specific? ;)

---

### Post by nikoPSK on 2008-01-14
> **crjackson said:**
> I just looked it up for you.  You need PC2100 DDR.

[http://www.memoryx.net/gamo15.html](http://www.memoryx.net/gamo15.html)

Thank you! Didn't notice. ;)

> **p_quarles said:**
> Given the size of the province of British Columbia (beautiful place, btw), I'd have to that "close to" it could include everything from Taipei to Reykjavik. You wanna be more specific? ;)

Sure, victoria. :p

---

### Post by crjackson on 2008-01-14
> **nikoPSK said:**
> I got there... :) Now what about recommended memory close to BC, canada?

I'd just order from here.  [http://www.crucial.com/store/listparts.aspx?model=GA-8IR2003](http://www.crucial.com/store/listparts.aspx?model=GA-8IR2003)

It's free shipping here for me, I don't know about BC.  However they are lifetime replacement for free, and micron chips.  I've used them for many years.  This is the page for your computer.

---

### Post by nikoPSK on 2008-01-14
> **crjackson said:**
> I'd just order from here.  [http://www.crucial.com/store/listparts.aspx?model=GA-8IR2003](http://www.crucial.com/store/listparts.aspx?model=GA-8IR2003)

It's free shipping here for me, I don't know about BC.  However they are lifetime replacement for free, and micron chips.  I've used them for many years.  This is the page for your computer.

Thanks! It's just that I need more that 512 megs. I can support up to 3 gigs, so might as well use em. :P

---

### Post by crjackson on 2008-01-14
> **nikoPSK said:**
> Thanks! It's just that I need more that 512 megs. I can support up to 3 gigs, so might as well use em. :P

You can't go wrong with crucial.

---

### Post by crjackson on 2008-01-14
Just remember, mixing old memory with new memory is problematic often time.

It's best to buy all at once and get matched sets from the same MFG lot.  This way the timing controller on each chip with sync properly.  Mixing older/newer is rolling the dice, and could leave you to think your new memory is defective when in fact it's not...

---

### Post by nikoPSK on 2008-01-14
> **crjackson said:**
> Just remember, mixing old memory with new memory is problematic often time.

It's best to buy all at once and get matched sets from the same MFG lot.  This way the timing controller on each chip with sync properly.  Mixing older/newer is rolling the dice, and could leave you to think your new memory is defective when in fact it's not...

that's fine by me. :)

---

