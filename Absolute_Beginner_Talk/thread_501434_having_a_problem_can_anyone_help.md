---
title: "having a problem can anyone help"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by fada basment on 2007-07-15
i just installed ubuntu on my laptop and the speakers doesn't work only when i use my headphones  what should i do to fix the problem laptop is a Toshiba L35-1054

---

### Post by JesterDev on 2007-07-15
Personally that sounds more like a hardware issue with you laptop more then a ubuntu problem. I have the same issue on my HP laptop, only the headphone jack does not work. 

Do your speakers work under other OS's? Have they worked before? 

What soundcard do you have? I always managed to fix sound issues with 'alsaconfig' under Suse. Can't seem find it under ubuntu however. Give me a second, I'll see if I can find it.

---

### Post by JesterDev on 2007-07-15
Load up a terminal window and type in this:

[php]
alsamixer
[/php]

What is the result?

---

### Post by fada basment on 2007-07-15
yes the speakers work with other systems i was running windows xp before and they worked fine

---

### Post by ReaderRat on 2007-07-15
Sorry, but the only info I could get on your Toshiba was in Arabic (I think). Does the Toshiba have an Intel Processor and Intel High Definition Audio (HDA)?

---

