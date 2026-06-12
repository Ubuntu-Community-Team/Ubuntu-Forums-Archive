---
title: "Trouble with starting Ubuntu"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by mickster on 2007-04-04
Hi, I have downloaded ubuntu 6.10 for desktop, but have trouble getting it to start.

I click on start or install ubuntu, and the linux kernal fully loads with no problems.
After that I get a black screen with just the following:

[17179569.184000] ACPI: Unable to locate RSDP

After a few seconds the Ubuntu name and logo come up with that bar with the orange thing going backwards and forwards.

After that (sorry this is dragging on a bit) I get a page with just line after line of errors.
The last couple of lines are as follows:

[ 574.091094] EIP: [<clef9a52>] 0xclef9a52 SS:ESP 0068:c064bcec
[ 574.091374]  <0> Kernel panic - not syncing: Fatal exception in interrupt
[ 574.091701]

After this nothing else happens, and my system stops responding.
Does anyone know why this happens or what I can do to stop it happening?

Cheers,
Mick.

---

### Post by oilchangeguy on 2007-04-04
found this:
[http://ubuntuforums.org/showthread.php?t=189190](http://ubuntuforums.org/showthread.php?t=189190)

---

### Post by mickster on 2007-04-04
Ok, after reading that thread I tried restarting with: "irqpoll and noacpi" boot options.

New Problems...

More lines of errors like these: (I'll post the screen pictures tomorrow if you like)

Then I get the flashing underscore thing, and I can type anything (US keymap) but nothing I type does anything.

Anyone have any other ideas?

---

### Post by jrandolph on 2007-04-04
I had some trouble on my install and all I had to do was type acpi=off after the boot line

---

### Post by Happy_Man on 2007-04-04
Perhaps your disc is corrupted? How fast did you burn it? If a cd is burned too fast, there's a good chance something's corrupted. I recommend burning reeeally slow, like 2x or 4x or so, and then trying.

---

### Post by mickster on 2007-04-05
> **jrandolph said:**
> I had some trouble on my install and all I had to do was type acpi=off after the boot line

I turned off ACPI and that got rid of the first error about RSDP before the ubuntu thing comes up, But now I get a new set of errors after that.

```
[ 616.894668] SQUASHFS error: zlib_fs returned unexpected result 0xfffffffd
[ 616.894860] SQUASHFS error: Unable to read page, block 1088900, size 54f7
[ 763.925295] SQUASHFS error: zlib_fs returned unexpected result 0xfffffffb
[ 763.935557] SQUASHFS error: Unable to read page, block fcd554, size 59cf
```

> **Happy_Man said:**
> Perhaps your disc is corrupted? How fast did you burn it? If a cd is burned too fast, there's a good chance something's corrupted. I recommend burning reeeally slow, like 2x or 4x or so, and then trying.

To answer this, I always burn important discs such as boot discs really slowly. I also checked the disc integrity on another computer and it was fine (the disc checking thing doesn't work on the computer i'm trying to run ubuntu on either.)

---

### Post by mickster on 2007-04-05
Does anyone know what i can do to get it working.

---

