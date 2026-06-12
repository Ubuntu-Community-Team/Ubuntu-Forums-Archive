---
title: "SSH Question"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by Tweek84 on 2006-11-15
Is it possible to SSH into an exsisting session? 

For example: I have user1 logged in on TTY2 running irssi, is it possible using SSH to log into that specific session and then log out without actually logging user1 out of the system at all?

I'd prefer to keep this to SSH since it's secure as a rock and my workplace definitely doesn't block the ports.

---

### Post by mahy on 2006-11-15
> **Tweek84 said:**
> Is it possible to SSH into an exsisting session? 


Not directly. You can use a util called 'screen' to detach one session, then log out, log back in via ssh and reattach the screen.

---

### Post by Tweek84 on 2006-11-15
Excellent, thanks!

---

