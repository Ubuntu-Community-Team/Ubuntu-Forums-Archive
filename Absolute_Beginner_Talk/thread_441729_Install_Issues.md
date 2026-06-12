---
title: "Install Issues"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by Noobinvader1 on 2007-05-12
I am trying to install ubuntu into my pc, i currently have it installed on my laptop and it is working perfectly, but when i try to install into my pc i get a message on my monitor that says "frenquency out of range: Hf 70.19 Khz - Vf 87.10 Hz. How do i change that so i can use the gui interface? when i hit conrol alt f2 or f3 i can go to the terminal window and that is about it. Any suggestions?](*,)

---

### Post by jtraub on 2007-05-12
try to load with different resolution on boot prompt

---

### Post by AAM on 2007-05-12
Noobinvader1, there are multiple causes for this problem. The one that corrected my problems was to append "irqpoll"* at the end of the boot sequence. You may also need to choose the safe graphics mode.

Just for interest, what screen resolution and what graphics card do you have?

*I should say that I have no idea what *irqpoll* is actually doing, except polling the irqs! (which likewise means nothing! Tried to find out but no luck!

---

### Post by Noobinvader1 on 2007-05-12
> **AAM said:**
> Noobinvader1, there are multiple causes for this problem. The one that corrected my problems was to append "irqpoll"* at the end of the boot sequence. You may also need to choose the safe graphics mode.

Just for interest, what screen resolution and what graphics card do you have?

*I should say that I have no idea what *irqpoll* is actually doing, except polling the irqs! (which likewise means nothing! Tried to find out but no luck!

How do you use IRQpoll? I do not know what that is. when i go into my computers hardware
it is an onboard video card that says Intel(R) 82865G Graphics Controller. I am running a HP D8904 17" Monitor and when i go into the display freq menu of it it says : HF- 60.05kHz, VF-75.03Hz @ 1024x768DPI.   
Maybe I should put my invidia Graphics card out of my other computer into this and see what it does?

---

### Post by Noobinvader1 on 2007-05-12
> **jtraub said:**
> try to load with different resolution on boot prompt

What resolution should i try it at? and how do i change it?

---

### Post by Noobinvader1 on 2007-05-14
Anyone have any hints or suggestions?:confused:

---

