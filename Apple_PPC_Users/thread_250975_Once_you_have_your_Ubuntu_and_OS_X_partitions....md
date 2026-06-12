---
title: "Once you have your Ubuntu and OS X partitions..."
date: 2006-09-04
forum: Apple PPC Users
---

### Post by beanmarine101 on 2006-09-04
How do you actually choose which one to boot from? Since I'm going to be the only one booting into Ubuntu, I'm going to make OS X the default system. However, how do I go about actually booting into Ubuntu?

---

### Post by Patch^ on 2006-09-04
hold/press the "alt" key (aka "option" key) Just as you turn on your mac. Then select the drive :)

Hope this helps :)

---

### Post by gThree on 2006-09-04
Yaboot (PPC) gives you a choice ... it waits for a set amount of time for you to input an "x" or an "l", and then boots the default.  Wait time can be altered.  Or you can go the Apple route by holding the ALT/OPTION key just after the start chime.

---

### Post by jpowermacg5 on 2006-09-04
I myself actually have a question about this.

I installed ubuntu on a different HDD, on a 4 GB partition.... I disconnected all 3 of my harddrives before installing ubuntu... but before I did.. I was trying to not load yaboot first by making the Hard drive I was going to install ubuntu on to load last..... though after I installed ubuntu..and connected my other drives back... Yaboot still manages to loads first somehow... but ovbiously didn't have a Mac option... so I had to edit yaboot.conf, and tell it:

macosx=/dev/hda3/
defaultos=macosx

then I restarted but it didn't work.. so I typed some ybin command.. and restarted.. and it worked.

But what I'd like to do... is not load yaboot first... how can i only load yaboot if I'm holding option down?

Even though my temp solution works pretty good... i don't want to trust yaboot for booting.. lol

---

