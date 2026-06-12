---
title: "Dapper shutdown freeze"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-11-18
When I click the red shutdown button from the desktop, it freezes 
and never shuts down. I've tried going through the terminal (sudo 
shutdown now) and it only results in it trying to halt and giving 
me the terminal prompt again. The only way to shut down is to ctrl
 alt backspace back to gdm and shutdown from there. any idea what 
could be wrong?

---

### Post by localuser on 2006-11-18
Did it ever work?  If so then what changed?

---

### Post by shanepardue on 2006-11-18
No, it's a clean install of Dapper. It never worked.

---

### Post by shanepardue on 2006-11-19
any idea how to fix something like this? I don't see how a clean install 
would have a problem such as this.

---

### Post by localuser on 2006-11-19
> **shanepardue said:**
> any idea how to fix something like this? I don't see how a clean install 
would have a problem such as this.

Others might know more but it sounds strange to me.  Did everything work properly off the livecd?

---

### Post by shanepardue on 2006-11-19
I don't recall if it did before I installed it, but it works on a live cd now!

---

### Post by localuser on 2006-11-19
> **shanepardue said:**
> I don't recall if it did before I installed it, but it works on a live cd now!

This is probably a really bad way to try to solve the problem, especially if you've already configured your system the way you like it, but...

what about a reinstall?  You say that this is a fresh install, how much effort have you put into configuring the system?

---

### Post by shanepardue on 2006-11-19
Yeah. I know that's an option, hehe. I'm hesitant, but I guess it's inevitable.

---

### Post by shanepardue on 2006-11-20
I figured out it was a problem with beryl and the aiglx setup i had with 
Dapper. I since installed Edgy with the built-in AIGLX and things work great!

---

