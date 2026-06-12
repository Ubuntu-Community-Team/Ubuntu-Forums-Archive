---
title: "What's the best way to do RAID?"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by diablo75 on 2008-02-28
I have never set up a raid array before, except RAID 1 I think under windows NT a long time ago.   I think.

Anyway, say I want to have a computer with two hard drives that mirror each other.  Can I do something like this in Ubuntu easily?  The goal is to create as much system fault tolerance as possible so the data will never be lost.  I would be willing to take this up a few notches if anyone has some suggestions about increasing data integrity in the event of a "system meltdown", if you know what I mean.  On the side, would the use of solid state hard drives be a worth while investment, or would using regular hard drives in a simple RAID array be more economical?

---

### Post by Fred_E _krugar on 2008-02-28
Well there is two ways that you can do this one is to use software raid (which I dont use).

Or you could use hardware raid (which is the one I prefer).

---

### Post by Fred_E _krugar on 2008-02-28
In fact this is the very card I am using with 6 80 gig hd in a raid 0 but it can also do raid 6.[http://www.newegg.com/Product/Product.aspx?Item=N82E16816131004](http://www.newegg.com/Product/Product.aspx?Item=N82E16816131004)

---

### Post by igknighted on 2008-02-28
Hardware raid is the way to go, I wouldn't even consider software raid.  Higher-end motherboards often have raid capabilities... explore your bios settings to see if yours does.

---

### Post by Fred_E _krugar on 2008-02-28
> **igknighted said:**
> Hardware raid is the way to go, I wouldn't even consider software raid.  Higher-end motherboards often have raid capabilities... explore your bios settings to see if yours does.

The onboard raid controllers are software raid that is why I dont  use mine( ICH9R).

---

### Post by igknighted on 2008-02-28
> **Fred_E _krugar said:**
> The onboard raid controllers are software raid that is why I dont  use mine( ICH9R).

On all boards?  I thought the nicer mobo's had real hardware raid chips on there...  I've only used raid on servers at work (and only real basic two disk raid1), never a desktop system, so I'm by no means the expert and could very easily be wrong

---

### Post by Fred_E _krugar on 2008-02-28
> **igknighted said:**
> On all boards?  I thought the nicer mobo's had real hardware raid chips on there...  I've only used raid on servers at work (and only real basic two disk raid1), never a desktop system, so I'm by no means the expert and could very easily be wrong


Well dont quote me but the only boards that I know that have Hardware raid onboard is supermicro.

On most of the raid chips are just a bios with the software raid  built in. the true hardware raid have a separate IO processor.

---

### Post by igknighted on 2008-02-28
> **Fred_E _krugar said:**
> Well dont quote me but the only boards that I know that have Hardware raid onboard is supermicro.

On most of the raid chips are just a bios with the software raid  built in. the true hardware raid have a separate IO processor.

thanks, i'll keep that in mind.

---

