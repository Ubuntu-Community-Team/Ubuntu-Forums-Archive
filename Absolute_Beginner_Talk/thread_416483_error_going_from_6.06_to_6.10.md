---
title: "error going from 6.06 to 6.10"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by RogerDavis on 2007-04-21
I'm trying to go from 6.06 to 6.10 to 7.04.

I can't even get to 6.10, I get the following error message:

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)

Can anyone help?

---

### Post by DougieFresh4U on 2007-04-21
How are you trying to upgrade?

---

### Post by RogerDavis on 2007-04-21
using update manager, from terminal, update-manager -c

I tried going to that web location, what I get is garbage that is probably code, so I can get there...

Thanks!

---

### Post by DougieFresh4U on 2007-04-21
Well why don't we try the "hacky way. Go into sources list and change all dappers to edgy and while your in sources list, whatever country is listed before (us) or none I put gb (great btrit) and I seem to have had no problems as servers are really swamped.  Once edgy is all through all the updates etc, do a **sudo apt-get update **then go back in sources list and change all edgy's to feisty. Let us know how you are doing and any prob post please

---

### Post by dwhsix on 2007-04-23
FYI, I got around this by doing a:

sudo apt-get clean

And then it worked fine.  I assume I a cached file that was corrupted somehow...

---

