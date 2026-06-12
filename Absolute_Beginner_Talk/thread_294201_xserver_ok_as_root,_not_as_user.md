---
title: "xserver ok as root, not as user"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by podunk on 2006-11-06
sort of a weird problem

I set up Edgy, and decided it was way to buggy for my tastes, so I am setting dapper back up, I'll try edgy again over the holidays when i have more time.

ran the set up cd, partitioned everything ok, restarted.

I get tot he log in screen, enter my user name and password, and it tries to log me in but then kicks me back to the log in. I chose fail safe start up, ran sudo depkg reconfigure xserver-xorg and restarted, same thing.

So I restarted in recovery mode, I was going to hand edit xorg.conf, but before I did for some reason I typed in startx and the desktop came up.

What would cause the xserver to run as root but not as user?

---

### Post by caravel on 2006-11-06
Permissions?

---

### Post by podunk on 2006-11-06
Thanks for the reply caravel - the permissions on the troubled machine are the same as the permissions on my working one?

---

### Post by taurus on 2006-11-06
Look in ~/.dmrc to make sure you own it and it has a permission of 600 (read/write for owner) or 644 (read/write for owner and read for group/world)...

---

### Post by podunk on 2006-11-06
That and couple of other things and I was able to get it limping along good enough to restore my back up and that fixed everything. Thank you! :-)

I wonder what I did to make it reintall so weird?

---

