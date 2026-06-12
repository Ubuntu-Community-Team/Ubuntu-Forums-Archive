---
title: "dual booting xp"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by Slander on 2007-10-24
hello all,

let me start by saying i'm 'almost' completely new to Linux.  I dual booted mandrake 9.0 back in the day with windows 2000, havent touched it since, so pretty much forgotten everything.  Now...I'm on a toshiba laptop running win xp sp2, trying to dual boot Ubuntu.  Got it installed, it loaded up fine while the live cd was in, the install seemed to be flawless.  After restarting the pc without the live cd, Grub comes up, lets me choose which OS to boot, I select the ubuntu os and then it acts like its going to load, it briefly flashes a bug message about ...hrm, didnt write the message down, was something about a clock?  I'll get the exact message and post it in a few minutes, after that message, it goes to a black screen, with no curser and no messages....

I'll brb with that error message

---

### Post by Arwen on 2007-10-24
Please post your graphics card and RAM as well..

---

### Post by Slander on 2007-10-24
512 MB ram
ATI Radeon Xpress 200m series

The error message i'm getting is:
MP-Bios Bug 8254: timer not connected to IO - APIC

I found a couple of entries for this in the forums here, but I'm not able to fix it with what was listed there.  It might work if I had a clue as to what I was doing but i dont lol.

I tried to edit the boot line to add 'noapic', the error message disappeared, but it still didnt load.  Was still stuck with the black screen with no cursor.

Any suggestions would be much appreciated

---

### Post by Slander on 2007-10-24
anyone able to assist me with this?

---

### Post by steve-shinn on 2007-10-24
> **Slander said:**
> anyone able to assist me with this?

What motherboard have you got there ?

Have you read this thread :-http://ubuntuforums.org/showthread.php?t=450748

---

### Post by Slander on 2007-10-25
I figured it out.  stupid windoze user that I am, I just wasnt waiting long enough for it to boot.  I figured out how to pull up the console so I could watch it load, its been loading up fine even with the APIC error.

---

