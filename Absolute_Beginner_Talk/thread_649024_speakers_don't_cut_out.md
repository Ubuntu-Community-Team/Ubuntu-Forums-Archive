---
title: "speakers don't cut out"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by idefixuk on 2007-12-24
When listening with headphones on my laptop the speakers don't cut out. I have Ubuntu 7.10 on a Toshiba Portege R500.

---

### Post by hfranco on 2007-12-24
Cut out?  Can you be more specific?

---

### Post by xeth_delta on 2007-12-24
My guess would be that he means the speakers don't mute when using headphones.

---

### Post by bobbocanfly on 2007-12-24
Normally speakers dont mute when you plug in headphones. You could try just sending audio the headphones by running:

```
alsamixer
```

Turn everything except the headphones down and you should get what you want.

---

### Post by xeth_delta on 2007-12-24
> **bobbocanfly said:**
> Normally speakers dont mute when you plug in headphones. You could try just sending audio the headphones by running:

```
alsamixer
```

Turn everything except the headphones down and you should get what you want.

Sorry, but I would not be so sure about that. In the laptops I've seen, and in particular the ones I've owned, the speakers will mute when you use headphones. You had the option to leave them unmuted.

Xeth

---

### Post by idefixuk on 2007-12-24
thank you!!!, I muted the front channel, in alsomixer, using the < > keys. :)

---

