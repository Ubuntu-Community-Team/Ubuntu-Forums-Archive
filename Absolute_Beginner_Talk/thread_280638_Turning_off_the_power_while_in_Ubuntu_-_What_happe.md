---
title: "Turning off the power while in Ubuntu - What happens next?"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by emarkay on 2006-10-19
OK, no smartypants answers like "the screen goes dark" or "you loose all your data"...

Window$, on rebooting, sends you a blue nastygram and then slowly checks each volume, and even then sometimes, leaves kipple and other crap on your disk(s).

What does Ubuntu do?

(and please, no smarty pants comments like "Flip the switch and find out for yourself.", either)  :)

MRK

---

### Post by kidders on 2006-10-19
Hi there,

Most Linuxes do almost nothing. Rudimentary disk checks are usually performed on boot, whether you shut down correctly or not, but beyond that,  there is no special recovery thingy or anything like that.

Windows does all sorts of things when you shut down improperly because, as I understand it, its filesystems aren't well-enough designed to guarantee consistency in the event of a sudden power loss.

Linux' filesystems on the other hand, are quite good at staying consistent. That doesn't mean you won't lose any data, but it does mean corruption is a bit less likely than you might be used to.

Is that any help?

Incidentally, feel free to give it a try, if you like. (I know you said you didn't want to hear this!!) Boot your machine, kill your X server, and let it sit there for a few minutes. If you kill the power all of a sudden, the disks should be fine, and you'll get to see first-hand how things behave. You won't notice anything spectacular though.

**Edit:** On some filesystems, a "Lost+Found" directory can sometimes appear ... this is the Linux equivalent of the "kipple" Windows leaves lying around. They're orphaned fragments of data that your box didn't know what to do with, but wasn't comfortable deleting, all the same.

---

### Post by louieb on 2006-10-19
Tuff my smarty pants answer is: Do you feel lucky? 

The real answer depends on what file system you are using and how much disk activity was in progress. For more info google/linux is your friend.

---

### Post by SoloSalsa on 2006-10-19
Nothing, for me at least.  I've done some forced offs when the computer was idle, and nothing happened.  I've never tried it while saving a document, or downloading, or during disk access, though.

---

### Post by emarkay on 2006-10-19
"Kinda sorta" what I thought.  
Another reason to flee fast from Window$
Thanks!

---

### Post by d3v1ant_0n3 on 2006-10-19
well this laptop has some major hardware flaw that I can't track down...Every so often, it will power off for no apparent reason. So far i've not noticed any major hiccups upon a reboot into Ubuntu.

Which is nice.

---

