---
title: "Return of a Geek"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by Tex_Johnson on 2007-12-17
OK.. So I have been around computers since the TRS-80 and the TI-994a.
I used to store my Code on my Dad's old Reel to Reel because cassettes were too small. :shock:

I got older... busier or lazier and moved away from CLI as a hobby but kept my Passion for PCs. I have recently felt the force returning me to *Nix
So here's my Question... Will todays Ubuntu/*nix run on Bleeding edge machines?
How difficult is the hunt for Drivers and Compilers?
Just for example... 

How does it handle Multiple Cores on Multiple processors? (ie AMD 4x4)
NVidia SLI Arrays?
SATA RAID?

and How stable is WINE these days on such a system?
I play ALLOT of winblows only games (Portal, CSS,  LOTRO, FEAR)
How stable is dual booting to an an array?

---

### Post by macogw on 2007-12-17
Drivers are usually included in the kernel.  ATI and Nvidia binary drivers are available from the restricted driver manager.  

For compilers, just install the build-essential package and you'll have gcc, make, autoconf, etc.

Multiple cores is fine

RAID depends on the controller

Wine works for some stuff, not for others.  Check out winehq.org to see what works and what doesn't.  WoW definitely works.

---

### Post by candtalan on 2007-12-17
Welcome!
Consider initial use of Live CDs initially? Go gently with the (re) learning curve. Take backups seriously, particularly before you start changing partitions or installing anything, maybe even just keep a tame windows machine to give yourself an easy life for the games you have.

---

