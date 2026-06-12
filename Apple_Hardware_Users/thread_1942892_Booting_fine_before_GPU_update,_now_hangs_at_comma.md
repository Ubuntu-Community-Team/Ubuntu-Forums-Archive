---
title: "Booting fine before GPU update, now hangs at command line, help!"
date: 2012-03-18
forum: Apple Hardware Users
---

### Post by razaz03 on 2012-03-18
Hi all,

After getting a new macbookpro 4,1 (nvidia supplying bad chips to apple and having the logic board reinstalled for free), I thought about giving this dual-boot malarkey another go.

Installed fine (11.10, bye bye windows), refit fine, everything fine.

Boot into desktop and what's this? drivers are available you say? So I install the recommended nvidia accelerated laptop rapers, reboot and it hangs at command line:

/dev/sda1: 10 files, 30993/403266 clusters

modem-manager starting...
...
...
Starting AppArmor profiles
...                                                                        [OK]
Stopping automatic crash report generation             [[COLOR=Red]fail[/COLOR]]

It just hangs at "Stopping restore sound card(s') mixer state(s)

blinking cursor.

Fail indeed. Did the *recommended *graphics drivers update screw me over? And if so how could I revert?

EDIT: The top of the command-line seems to be a fsck, declaring my sda4 (ubuntu parittion) clean. It seems to trip itself up on sda1 - I'm assuming that's my EFI partition. Apologies as I do not remember where error logs are stored.

---

### Post by razaz03 on 2012-03-18
Bumpety please and thanks, gonna link this in the main forums in case it is simply a graphical issue, but please respond!

---

### Post by razaz03 on 2012-03-19
Tried again, fsck now displays another fail at 'starting CPU interrupts balancing daemon', even though my /dev/sda4 (ubuntu) is being displayed as clean.

Nobody knows how to bypass fsck (tried googling) or what's the actual issue here?

---

### Post by critin on 2012-03-21
> After getting a new macbookpro 4,1 (nvidia supplying bad chips to apple and having the logic board reinstalled for free),

Sorry you're not getting answers here.  I can't help with macbook, but--did you use the book sufficiently to know that all was right with it after receiving it back ?  Could there still be some sort of issue with the machine itself?

Is 11.10 the only OS on the system?  If so, and if it was mine, I'd insert the live cd/flash and reinstall.  And then play with it for awhile, do not install the recommended drivers until you know for sure you need to.  (sometimes you don't)

---

