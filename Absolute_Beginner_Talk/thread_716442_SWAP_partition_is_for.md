---
title: "SWAP partition is for?"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by NautTboy on 2008-03-05
I see you need 2 partition, linux and swap to install linux.  Why do we need the swap.  I mean what is its purpose?

It might be a dumb question but I'm trying to learn.

---

### Post by vishzilla on 2008-03-05
read about it [here]("http://www.linux.com/feature/121916")

---

### Post by fissionmailed on 2008-03-05
It's virtual RAM, so when you run out of RAM, it stores the information on the hard drive.  Which makes accessing the information a lot slower due to the system bus being much faster than the peripheral bus which the hard drive is on.  

Make sense?

---

### Post by Google Spider on 2008-03-05
Just like windows uses page file.

---

### Post by NautTboy on 2008-03-05
> **fissionmailed said:**
> It's virtual RAM, so when you run out of RAM, it stores the information on the hard drive.  Which makes accessing the information a lot slower due to the system bus being much faster than the peripheral bus which the hard drive is on.  

Make sense?

Thanks alot fissionmailed.

I got one more question.  I just got done installing slackware.  I rebooted.  How do i go into the X windows? Such as win from dos for Windows -XP

---

### Post by fissionmailed on 2008-03-05
> **NautTboy said:**
> Thanks alot fissionmailed.

I got one more question.  I just got done installing slackware.  I rebooted.  How do i go into the X windows? Such as win from dos for Windows -XP

No worries.

Sadly, I don't know that, I'm even goingto be install Slackware or FreeBSD on this laptop in the next couple of days too. doh...

---

### Post by Meatshield on 2008-03-06
> **NautTboy said:**
> Thanks alot fissionmailed.

I got one more question.  I just got done installing slackware.  I rebooted.  How do i go into the X windows? Such as win from dos for Windows -XP

I don't use SlackWare myself, but for most systems you login in the console then type:

```
startx
```

and it will boot into your window manager. Try that.

---

### Post by NautTboy on 2008-03-06
New thread has been open for startx

Thread closed.

---

