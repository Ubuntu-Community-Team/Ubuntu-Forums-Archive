---
title: "Help after install"
date: 2009-01-21
forum: Apple Hardware Users
---

### Post by SNAFU0062000 on 2009-01-21
I was able to install the Ubuntu 8.10 pwoerPC but after install and trying to boot it comes to i white screen show it looding but then when it gets to prom_init the computer turns off. what should i do.

---

### Post by sduensin on 2009-04-29
> **SNAFU0062000 said:**
> I was able to install the Ubuntu 8.10 pwoerPC but after install and trying to boot it comes to i white screen show it looding but then when it gets to prom_init the computer turns off. what should i do.

I've got the exact same problem.  The box was running Debian and OSX just fine.  Figured I'd try Ubuntu on it.  :-(

Anybody?

Scott

---

### Post by stream303 on 2009-04-30
Most likely culprit - the infamous Ubuntu splash screen.

When you reach the second-stage yaboot boot: prompt, (hit TAB to stop the automatic countdown), can you bypass the splash screen by entering:

```
Linux nosplash
```

and seeing if you make any progress that way?

---

### Post by sduensin on 2009-04-30
> **stream303 said:**
> Most likely culprit - the infamous Ubuntu splash screen.

When you reach the second-stage yaboot boot: prompt, (hit TAB to stop the automatic countdown), can you bypass the splash screen by entering:

```
Linux nosplash
```

and seeing if you make any progress that way?

That did it!  Thank you!  The PowerBook lives again!

Scott

---

### Post by stream303 on 2009-04-30
Great!

To make that kernel parameter permanent so you don't have to do this at every boot, change *splash* to *nosplash* in /etc/yaboot.conf and follow up with *sudo ybin -v*  In a terminal:

```
sudo nano /etc/yaboot.conf
```

Make the change to both of the APPEND= lines, and use CTRL-O to write it out, and CTRL-X to exit the nano editor.

Then make the system aware of that change with:

```
sudo ybin -v
```

and reboot.

There may be other issues with 8.10 for you, and if there is, you can drop back to 8.04 LTS, or perhaps try the latest 9.04.

Until Ubuntu realizes that the splash screen does more harm than good on PPC, you'll end up doing this for each release with that PowerBook.

---

