---
title: "Root Kits"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by jazzman84116 on 2007-06-08
Can root Kits effect the Linux kernel?

---

### Post by rich.bradshaw on 2007-06-08
Yep.

They can't automatically install themselves though - you'd have to either have someone deliberately install it, or sudo some dodgy file.

Most likely case is that you get your ssh bruteforced, then your root password guessed, then someone installs it.

you can use chkrootkit to check for a rootkit.

---

### Post by crispy_420 on 2007-06-08
They will work if you install them as root. But unless you really make attempt to install, they are nothing. Right now I would consider them more proof of concept. They may have been made just to be made.

---

### Post by RTrev on 2007-06-08
> **rich.bradshaw said:**
> Yep.

They can't automatically install themselves though - you'd have to either have someone deliberately install it, or sudo some dodgy file.

Most likely case is that you get your ssh bruteforced, then your root password guessed, then someone installs it.

you can use chkrootkit to check for a rootkit.

I just downloaded and tried chkrootkit, and all looked well except for this puzzling final line of the report:

```
Checking `z2'... user root deleted or never logged from lastlog!
```

Mean anything?

---

### Post by matchstich on 2007-06-20
when i had  dapper i installed automatrix  or however it is spelled,  and  chrootkit and  rkhunter both found a rootkit on my system.

don't remember what it was called.

won't make that mistake again.

---

### Post by chinaski on 2007-07-30
are you sure?

I have edgy + automatix and just scanned the system with chkrootkit and found nothing

I think you are wrong, as automatix is great and reliable software

---

### Post by Seisen on 2007-07-30
> **RTrev said:**
> I just downloaded and tried chkrootkit, and all looked well except for this puzzling final line of the report:

```
Checking `z2'... user root deleted or never logged from lastlog!
```

Mean anything?

If you haven't used the root account or logged in as the root account that message will show up. It would show up with you username that you use now if you didn't use it for a while. It's really nothing to worry about unless an account name that you don't recognize shows up.

---

### Post by RTrev on 2007-07-30
> **Seisen said:**
> If you haven't used the root account or logged in as the root account that message will show up. It would show up with you username that you use now if you didn't use it for a while. It's really nothing to worry about unless an account name that you don't recognize shows up.

Thanks!

---

### Post by MianoSM on 2007-08-07
I am getting "not tested: can't exec ./ifpromics for the sniffer, as well as for the chkwtmp, chklastlog, and chkutmp. 

When I ls the directory it looks like they all end in a .c so they look like this:
ifpromisc.c
chkwtmp.c
chklastlog.c
and chkutmp.c 

Am I messing this up, or did I forget a step?

---

### Post by MianoSM on 2007-08-07
> **MianoSM said:**
> I am getting "not tested: can't exec ./ifpromics for the sniffer, as well as for the chkwtmp, chklastlog, and chkutmp. 

When I ls the directory it looks like they all end in a .c so they look like this:
ifpromisc.c
chkwtmp.c
chklastlog.c
and chkutmp.c 

Am I messing this up, or did I forget a step?

The issue was that I needed to apt-get install gcc, as well as the devel tools. : )

Issue resolved, and system secure. : )

---

### Post by addux on 2007-12-09
> **Seisen said:**
> If you haven't used the root account or logged in as the root account that message will show up. It would show up with you username that you use now if you didn't use it for a while. It's really nothing to worry about unless an account name that you don't recognize shows up.

What If I have logged on and it still says this, for example I had to log on as root to use the program.

---

