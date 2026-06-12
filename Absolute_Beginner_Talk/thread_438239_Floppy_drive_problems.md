---
title: "Floppy drive problems"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by Noname02 on 2007-05-09
Ok folks- As a Ubuntu n00b, one last go at this before I use my Ubuntu disk as a birdscarer and find something else to load in the box. Been trying for days to get a handle on this but think I'm getting somewhere at last but need some input now. I was going to dump Linux and all it's works..but this has kinda got me fascinated....

I goes like this:

Version: Unbuntu V 5.10
Problem: System appears to not recognise FDD. everything else (appears) to be ok as far as it's gone. No attempt at online access devices yet. (I daren't!)

Tests: dmesg grep fd   (in terminal) gives output: [-C] [-N level] [-S bufsize]
Rightclick FDD in browser > Properties gives: Quantum Fireball 3.6 gB (!)

Conclusion: Unbuntu thinks the FDD is the hard drive hence cannot mount it. (!!) Incidentally, the Hard drive does appear where it's supposed to also, as does the CD Rom. 
 Before anyone asks, yes, the FDD is plugged into the OBFDD controller as usual! oh yes as well- swopped the FDD and cable for another identical one- still the same.

To give it it's due, it does TRY to read the disk in the drive before giving up so it's got that bit right at least....

Question: How to put it right! I did read on the forums about a bug in some Ubuntu versions affecting FDD's. Is this it..or something else entirely? 
Yours 
A morbidly fascinated failed Ubuntu user..

---

### Post by Martin on 2007-05-10
and you've checked fstab and made sure thats all in order? That Quantum stuff is a bit odd.

---

