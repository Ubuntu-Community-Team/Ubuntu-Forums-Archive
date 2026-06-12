---
title: "live cd installation"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by Teegro on 2007-03-27
I can get my copy of ubuntu dapper to run as a live cd on my laptop and  it runs quite well but whenever i try to actually install it the installer freezes up when i'm finished part 3.

The rest of the live environment still runs, i can quite happilly minimize the installer and play around with anything else thats on it till my hearst content but the installer refueses to budge.

I've tried the cd in my desktop and it boots and goes past the probomatic stage (keyboard setup) and onto the account setup screen so its not the disk. 

Is there any way to bypass the keyboard setup screen altogether and do it at a later date or is there some way i can copy everything to the hd and then install from there without a cd? it might just get sorted then.

Ive already tried the alt install for it but it doesn't install the desktop and comes up with an error saying theres no session data or similar.

any other theories as how to get it on would be greatly appreciated!

I'm running a dell lattitude with 500mhz p3, 128mb, 6.4gig hd and 8mb ati mobility.

---

### Post by Bachstelze on 2007-03-27
Those specs are not high enough for the installatioon via Live CD. Try the Alternate.

---

### Post by Teegro on 2007-03-27
already tried it. it installs fine but either the desktop isn't actually installed or theres a compatibility problem because it says theres no session data.

sudo startx

---

### Post by Bachstelze on 2007-03-27
Don't do that. To start your X, do

```
sudo /etc/init.d/?dm restart
```

---

### Post by Teegro on 2007-03-27
why do i never have any luck with linux?

---

