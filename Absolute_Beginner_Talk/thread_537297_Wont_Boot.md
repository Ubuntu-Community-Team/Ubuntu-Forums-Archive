---
title: "Wont Boot"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by redfox1160 on 2007-08-28
my computer was runing ubuntu 7.04 fine, then my brother was looking at screensavers and went to preview one. when he did it froze up, so he turned it off. when he turned it back on, it got to the screen where it says to hit delete to access the bios (not part of ubuntu) and it just says Wait... .It stays there and doesnt go any further, does anyone know what i should do? Please Help!

---

### Post by dwhitney67 on 2007-08-28
Is this still an ongoing problem?  Did you try to recycle power again to the PC?

It's unlikely that your brother could have affected the boot loader (grub) by just perusing screen savers.  Is it possible that the HDD is going bad?

If the problem persists, see if you can boot using the LiveCD.  If so, then afterwards you can try to mount the drive on the HDD where the Ubuntu distro lives so that it can be examined.

---

### Post by redfox1160 on 2007-08-28
how do i recycle power? leave the power out for a minute then plug it back in (thats how i power cycle my modem...)

---

### Post by dwhitney67 on 2007-08-28
Recycle... sorry poor choice of wording.  Maybe it's the near-empty bottle of beer next to me.

I should have stated "cycle power", which in the engineering world means to power off and then power on the device.

---

### Post by redfox1160 on 2007-08-28
yeah i have...

---

### Post by dwhitney67 on 2007-08-28
Your avatar makes you resemble a "deer in the headlights".  Have you attempted to boot with the LiveCD?

---

### Post by redfox1160 on 2007-08-28
not yet...

EDIT: It doesnt get far enough to boot from the cd... it says wait before that (i dont know if it has anything to do with ubuntu or not...)

---

### Post by redfox1160 on 2007-08-28
anyone have any suggestions?

---

### Post by irish_flu on 2007-08-28
Does it give you any odd/different "beeps" while it's sitting there at the "hit DEL to see the BIOS" bit?

If it does, this is called a "beep code" and signifies a hardware problem.  Most computers will emit a single "beep" when they boot; this is normal.

If it doesn't, it's still perhaps a problem with the hardware; my guess would be that it can't find one of the hard drives it's considering booting to.  It could also be a problem with the RAM, or maybe even your video card.

Some suggestions:
- if you have an external (USB) hard drive connected, unplug it from the computer and try again.

- if you're comfortable working inside the machine, make sure everything is seated properly and that all cables are connected.

Can you get into the BIOS?  Off the top of my head, it sounds like this might be a hardware issue.

---

### Post by redfox1160 on 2007-08-28
> **irish_flu said:**
> Does it give you any odd/different "beeps" while it's sitting there at the "hit DEL to see the BIOS" bit?

If it does, this is called a "beep code" and signifies a hardware problem.  Most computers will emit a single "beep" when they boot; this is normal.

If it doesn't, it's still perhaps a problem with the hardware; my guess would be that it can't find one of the hard drives it's considering booting to.  It could also be a problem with the RAM, or maybe even your video card.

Some suggestions:
- if you have an external (USB) hard drive connected, unplug it from the computer and try again.

- if you're comfortable working inside the machine, make sure everything is seated properly and that all cables are connected.

Can you get into the BIOS?  Off the top of my head, it sounds like this might be a hardware issue.

no, it doesnt beep. and no, i cant get in the bios. when it says hit delete to see bios it doesnt let me access the bios. then that changes to wait (weather i hit del or not...)

Should i try resetting the bios? (ive done it before...)

---

### Post by irish_flu on 2007-08-28
> **redfox1160 said:**
> no, it doesnt beep. and no, i cant get in the bios. when it says hit delete to see bios it doesnt let me access the bios. then that changes to wait (weather i hit del or not...)

Should i try resetting the bios? (ive done it before...)

If I were to guess (and it is a guess) the BIOS is not the problem.

First thing first, disconnect anything you don't absolutely need to run (network cable, printer, external stuff of all kinds).

Try to boot with nothing but the power cord, keyboard, and monitor cable connected.  Any difference?

---

### Post by redfox1160 on 2007-08-28
> **irish_flu said:**
> If I were to guess (and it is a guess) the BIOS is not the problem.

First thing first, disconnect anything you don't absolutely need to run (network cable, printer, external stuff of all kinds).

Try to boot with nothing but the power cord, keyboard, and monitor cable connected.  Any difference?

nope...:cry:i was so happy i finally got this computer working then this happens:cry:

---

### Post by irish_flu on 2007-08-28
Are you comfortable removing components from inside the machine?

---

### Post by redfox1160 on 2007-08-28
> **irish_flu said:**
> Are you comfortable removing components from inside the machine?

yes, i built the computer from old parts (probably part of the reason it doesnt work...)

---

### Post by irish_flu on 2007-08-28
Excellent.  BTW I've been there, buddy.

The first place I'd look is at the drives.  The easiest thing to do is to disconnect your IDE and/or SATA cables from the motherboard and see if she boots.

Of course, she won't boot all the way with no drives, but at least you should get a warning about no operating system being found.  If it has a floppy, you might disconnect that too.

If it works, great.  Connect the drives one-at-a-time until you isolate the problem.

If there's no difference with all of the drives disconnected reconnect them and then the next place I'd look is at my RAM.  If you have two sticks, take one out and boot.  Then switch.  If it works with one but not the other, you have your culprit.

---

### Post by irish_flu on 2007-08-28
If neither of those tests make any difference, start removing any PCI/AGP cards one at a time; is your video on a card, or is it built onto the motherboard, or do you have both?

---

### Post by irish_flu on 2007-08-28
BTW if anything I say is confusing in any way, ask.

---

### Post by redfox1160 on 2007-08-28
Thank You Sooooooo Much! When i unpluged the HDD cable then pluged it back in, it worked! I never would have thought of that! thank you so much!

---

### Post by irish_flu on 2007-08-28
GREAT, no problem there friend.  Probably it was just a little loose.  :)

---

