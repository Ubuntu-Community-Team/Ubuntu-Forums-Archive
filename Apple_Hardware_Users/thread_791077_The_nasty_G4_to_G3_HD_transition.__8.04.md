---
title: "The nasty G4 to G3 HD transition.  8.04"
date: 2008-05-11
forum: Apple Hardware Users
---

### Post by stevejesus on 2008-05-11
So I have this iBook that I am trying to resurrect for the express purpose of playing SMS games in the throes of lethargia (my bed).  The CD drive does not function.

Here is what I did, and also what went wrong...

After trying several things that I would later learn open-firmware is not capable of, I decided to extract the hard-drive from the iBook and attach it to a G4 tower.

The idea was to install 8.04 server to the disk from the host and then place the hard disk back in its home in the G3.

This should have worked...  The G3 and the G4 are very similar processors.  The only real differences between the G3 in my iBook and the G4 in my tower are cache-size/speed, and Altivec.  Besides, Ubuntu is configured by default to boot into a generic PPC kernel on 32-bit machines, so I should be able to boot this kernel on a 604e if i wanted to.

Anyway, the disk boots fine in the G4, but it doesn't make it's way out of Yaboot in the iBook.  Is there anything that I can do from Yaboot to force it to carry-on?

---

