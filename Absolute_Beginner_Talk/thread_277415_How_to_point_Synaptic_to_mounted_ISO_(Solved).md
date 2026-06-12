---
title: "How to point Synaptic to mounted ISO (Solved)"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by peeps on 2006-10-14
I'm "almost ready" to put a Mini ITX PC in my car, but I won't be having a DVD Rom drive connected to the motherboard when it goes in.  From time to time though, I may need access to some of the packages for Ubuntu, so I copied the Ubuntu ISO to another partition.

After doing a search, I found out how to mount the ISO, and I do it with:

sudo mount -o loop /media/hda5/Ubuntu/UBUNTU-6.06-DVD-I386.ISO /media/hda5/Ubuntu/

How do I point the Synaptic Package Manager to this mounted ISO as a repository?

TIA. :)

---

### Post by K.Mandla on 2006-10-14
There's an *apt-cdrom add* command, but I believe this is hard-wired to scan your CDROM drive. Hmm. ... :-k

Edit: Okay, there seems to be a -d option that will allow you to set a mount point. Would that work?

---

### Post by peeps on 2006-10-14
Thanks for the quick reply, K.Mandla.

But I wasn't sure of the -d switch option, so did:

synaptic -h

for the help file. Help is poor to say the least, but I saw a --add-cdrom switch and did this:

sudo synaptic --add-cdrom /media/hda5/Ubuntu/

It works.............Haha. So problem solved.

---

