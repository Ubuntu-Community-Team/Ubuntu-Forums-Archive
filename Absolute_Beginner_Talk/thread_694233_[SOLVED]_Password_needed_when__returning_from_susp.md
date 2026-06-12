---
title: "[SOLVED] Password needed when  returning from suspend?  How to bypass that?"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by RichTJ99 on 2008-02-11
Hi,

Thanks to the great user support on this forum, I am able to get my laptop back from suspend mode.

My normal boot up bypasses the startup screen login, I noticed when coming back from suspend, it asks for a password.

How can I make it so when it comes out of suspend, it logs itself in & goes back to the desktop?

Thanks,
Rich

---

### Post by smartboyathome on 2008-02-11
I don't think you can, at least not graphically. When going into suspend, I think it locks your screen, which means it requires your password.

---

### Post by oedha on 2008-02-11
want to try this ?
go to applications>accesories>terminal
type gconf-editor
go to the key at /apps/gnome-power-manager
look for lock_on_hibernate, disable it...

---

### Post by RichTJ99 on 2008-02-11
Excellent!  I just disabled everything in that section & it works perfectly!  Just how i wanted it!  

I might actually be done with Windows now.  My last problem to overcome is using Outlook with MS exchange.

---

### Post by oedha on 2008-02-11
so...is this thread solved ?
can you scroll up and click on thread tool and mark this thread solved ?
thank you

---

