---
title: "NFSD: starting 90-second grace period"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by readitsideways on 2007-06-22
Hi

Anyone know what's causing this? The login splash screen stays there for a few minutes while none of the startup sessions run - so no windows manager, wireless, gaim etc.

My kern.log has:

 ppdev: user-space parallel port driver
apm: BIOS not found.
Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
NFSD: starting 90-second grace period
NET: Registered protocol family 10


I've tried reinstalling nfs-client ($ sudo apt-get --reinstall install nfs-client) and portmap but no luck.

Duncan

---

### Post by CoolkcaH on 2007-06-30
I have the same problem from about a week or two...I think it was an update that caused this.

---

### Post by readitsideways on 2007-07-12
Yep, it just sorted itself out. Must have been an update issue

---

### Post by ironmonkeygf on 2007-07-12
When did it sort itself out for you?  I've had what I believe is this problem since the middle of last week.  Hopefully Ubuntu will fire right up when I get home from work....but last night it was still slow to login.

---

### Post by ironmonkeygf on 2007-07-12
Still isn't fixed for me...

Anything else you might have done to fix it?

---

### Post by ironmonkeygf on 2007-07-12
I finally got mine fixed.  Somehow my wired connection got enabled.  I unchecked the box for my wired connection in System>Administration>Network and the slow login is gone.  Apparently the 90-Second GracePeriod had nothing to do with the slow desktop because I still get that message in kern.log.  Hope this helps someone...

---

### Post by readitsideways on 2007-07-13
Ah, it's possible that that was my problem too...

---

