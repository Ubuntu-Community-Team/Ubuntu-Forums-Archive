---
title: "Sound problem"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by Forko on 2006-08-11
I just upgraded to Dapper from Breezy, and now all of the sound is panned to the left. I can't find a control to change it, what should i do?

---

### Post by klytu on 2006-08-11
> **Forko said:**
> I just upgraded to Dapper from Breezy, and now all of the sound is panned to the left. I can't find a control to change it, what should i do?
 
Depending on your exact set-up there could be a couple different ways to control the master volume. Here's one you can try which works on many set-ups. Type this is a terminal console:

```
aumix
```

Use the up and down keyboard arrows to select which item you want to adjust; left and right keyboard arrows adjust down or up.

---

### Post by depele on 2006-08-11
same problem here but I have no sound anymore, and he doesn detect any sound driver 

aplay -l
aplay: device_list:221: no soundcards found...

lspci -v
gives this by sound.
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 7010
        Flags: bus master, medium devsel, latency 32, IRQ 3
        I/O ports at e400 [size=256]
        I/O ports at e800 [size=128]
        Capabilities: <available only to root>

can some body help me please. 
thanks

---

### Post by depele on 2006-08-12
anyone who could help?

---

### Post by klytu on 2006-08-12
> **depele said:**
> same problem here but I have no sound anymore, and he doesn detect any sound driver 

aplay -l
aplay: device_list:221: no soundcards found...

lspci -v
gives this by sound.
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 7010
        Flags: bus master, medium devsel, latency 32, IRQ 3
        I/O ports at e400 [size=256]
        I/O ports at e800 [size=128]
        Capabilities: <available only to root>

can some body help me please. 
thanks

[This thread]("http://ubuntuforums.org/showthread.php?t=188124") might help you. Try searching the forum for your exact sound card. It appears a number of folks with sound controllers similar to yours have had difficulty since a recent kernel update.

---

