---
title: "Disk not cleanly unmounted"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by dosmode on 2007-03-03
> hda3 was not cleanly unmounted, check forced.
I just recieved the above messaged when I booted to Ubuntu and it did what seemed like a check of hda3 which is my Linux root drive and did not complete the check when it gave me a message that [COLOR="Red"]something died[/COLOR], in red.. I didn't get what it was that died but it went on to the login window.  Now, my dog just died a couple days ago and it wasn't a pleasant experience and I am hoping that this isn't something as serious.  Any ideas what that message means?  Thanks...

---

### Post by kinematic on 2007-03-03
without knowing the exact message no one will be able to help.

---

### Post by moshuptrail on 2007-03-03
The first message simply meant that the disk was not properly unmounted last time the computer shut down.  Maybe the sutdown didn't work?

Perhaps the key is what died.  I think a "tail /var/log/syslog" might tell you.  I think that's the one that gets written at boot time.  Maybe someone knows better and correct me...

---

