---
title: "Macbook Pro not shutting down, anybody else?"
date: 2008-04-22
forum: Apple Hardware Users
---

### Post by russo.mic on 2008-04-22
Just wanted to get some confirmation about Kubuntu Hardy RC

I had started a thread earlier about my MBP Pre-santa rosa not shutting down.  I figured out if I disable the ATI driver, it shuts down fine.  Wanted to see if anybody else had this issue before I filed.

Russo

---

### Post by russo.mic on 2008-04-25
So,  I've just done a reinstall today, and with 3d accel on, my laptop won't shut down on it's own.  I'm I really the only one?

---

### Post by cyberdork33 on 2008-04-25
> **russo.mic said:**
> So,  I've just done a reinstall today, and with 3d accel on, my laptop won't shut down on it's own.  I'm I really the only one?

So far you are the only one that has been complaining about this (unfortunate, sort of). Did you do a completely fresh install? what graphics are you using?

---

### Post by russo.mic on 2008-04-25
I was having the problem with the RC, so I did a clean install last night, and i've got the ATI restricted driver working.  the funny thing is, my hibernate and suspend work great for the first time ever out of the box!  but for some reason I can't shut down.  I've been opening up tty1 and just doing a sudo shutdown now.

For the most part, that ususally shuts down no problem.  every now and then, it hangs.  Do you know how I could do a verbose shutdown out of X as to troubleshoot the problem?

Thanks!

Russo

---

### Post by cyberdork33 on 2008-04-25
> **russo.mic said:**
> I was having the problem with the RC, so I did a clean install last night, and i've got the ATI restricted driver working.  the funny thing is, my hibernate and suspend work great for the first time ever out of the box!  but for some reason I can't shut down.  I've been opening up tty1 and just doing a sudo shutdown now.

For the most part, that ususally shuts down no problem.  every now and then, it hangs.  Do you know how I could do a verbose shutdown out of X as to troubleshoot the problem?

Thanks!

Russo
so, when you said 3d accel, did you mean the drivers or compiz?

when you startup and see the grub menu, hit 'e' and you can edit the config lines. remove the 'silent' and 'quiet' options from the kernel line and you will see all the console messages during startup and shutdown. That may give you an indication of where it is hanging.

---

### Post by russo.mic on 2008-04-25
I didn't know that would verbose shutdown as well!  Good to learn something new.  I'll do some troubleshooting, and post shortly

Thanks CD!

Russo

---

### Post by russo.mic on 2008-05-01
So,  I don't even get to the system shutdown report, as KDM doesn't always shutdown.  

Damn. 

Any ideas?

Thanks in advance!

Russo

---

