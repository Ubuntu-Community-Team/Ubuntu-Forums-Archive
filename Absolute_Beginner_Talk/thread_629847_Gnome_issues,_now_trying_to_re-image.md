---
title: "Gnome issues, now trying to re-image"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by japtar10101 on 2007-12-02
I have some gnome-based issues: every graphical errors I have (including freezing, inability to change themes, glitchy window graphics, and so forth) resides from ubuntu than kubuntu.  The errors began when I've updated from Feisty to gutsy Gibbons, and I believe part of the problem resides from some odd configuration I've had in the past clashing with the present (I want to point a finger at compiz-fusion and xgl, but I frankly don't know.  I did remove the xgl session codes, but the problem still exists).

If anyone has any suggestions to solve this part, any explanation (or clarification) will be greatly appreciated.

Anyway, out of frustration, I decided to re-image the whole thing...until I realize when I boot from the Gutsy CD (and my past Feisty Fawn image I've used to install the OS I'm using now), nothing happens.  I get a blank screen, and absolutely no menu prompt.  So now I have a glitchy desktop AND a computer that can't be re-imaged.

This is even more frustrating.  I think I'll end up trying to boot a vista CD if this whole thing continues....

(Note: I realize the latter is more of a system issue.  Like I've said, I did use the same CD to boot up the computer in the past, and that didn't read.  I was wondering if, by chance, magnets have any effect in harming a desktop.  I kept a magnetic whiteboard posted on the desktop, and I think that may have been what caused it....)

EDIT: Ha, ha....I've figured out the problem.  I misplaced the Cd-drive's SATA connection.  That would explain everything...

---

### Post by thelatinist on 2007-12-02
If I understand correctly, you are unable to boot from the same live cd you successfully booted from in the past on the same hardware.  If that's the case, and if you haven't changed anything in bios, then it's likely a problem with the CD itself.  Try redownloading and burning again at 4x.

---

### Post by japtar10101 on 2007-12-02
> **thelatinist said:**
> If I understand correctly, you are unable to boot from the same live cd you successfully booted from in the past on the same hardware.  If that's the case, and if you haven't changed anything in bios, then it's likely a problem with the CD itself.  Try redownloading and burning again at 4x.

I have two CDs, and neither of them work. One is old, and just as you've said, yes, it is the one I'm trying to re-use.  The other is a newly burnt Gutsy Gibbons for PC (I know my computer uses intel dual core processor), and that didn't run either.  It's interesting that, for some reason, OS seems to recognize that there are contents in the CD, but not the bios itself....

Anyway, downloading the .iso file is so time consuming, and I do have many other things to do.  I'll attempt to try again next week.

---

### Post by japtar10101 on 2007-12-03
I was talking to another person on imaging a computer.  Is my troubled coming from the fact that the the computer I'm using a ubuntu CD on a Ubuntu OS?

---

### Post by OffAxis on 2007-12-03
> Is my troubled coming from the fact that the the computer I'm using a ubuntu CD on a Ubuntu OS?
no.
If you're booting off the CD it really doesn't care what's on the hard drive (initially).

> I get a blank screen, and absolutely no menu prompt.
No menu prompt at all?
Sounds like a bad burn, BIOS setting, or hardware issue.

Can you boot anything on the CD drive? Like a supergrub disk?
[http://supergrub.forjamari.linex.org/?section=download]("http://supergrub.forjamari.linex.org/?section=download")

---

### Post by japtar10101 on 2007-12-03
> **OffAxis said:**
> no.
If you're booting off the CD it really doesn't care what's on the hard drive (initially).


No menu prompt at all?
Sounds like a bad burn, BIOS setting, or hardware issue.

Can you boot anything on the CD drive? Like a supergrub disk?
[http://supergrub.forjamari.linex.org/?section=download]("http://supergrub.forjamari.linex.org/?section=download")

As far as I know, the disk works on my laptop.  Since both computers have a dual core processor, I know that if the cd boots on my laptop, then the same should go for the desktop.  Unfortunately this isn't the case.  My conclusion is a hardware error, but I'll have to test this out more.  The CD/DVD reader seems to work fine (when I boot up KDE, which magically works fine, and read off the disc, I can see all of its contents intact), so it probably lies on the processor, graphic card (which is most likely why Gnome is dead) or the motherboard.

By the way, what's a super-grub?  In the case that this disc DOES boot, what do I do with it?

Thanks for the suggestions, I'll keep trying.

---

