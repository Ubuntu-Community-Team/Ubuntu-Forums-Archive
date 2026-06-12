---
title: "Xubuntu crashing"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by elBorba on 2007-02-11
I just installed Xubuntu 6.10 onto a PII 400 Mhz with 385 meg of ram.  The install seemed to go okay from the "alternate" CD,  However, when I try to log on, sometimes the GUI  trys to launch, blinks a few times, then kicks me back to the log in screen.  Or sometimes the GUI manages to launch, but after a little while (minutes) blinks a few times and kicks me back to the login screen.

Any ideas how I can go about fixing or tracking down the issue?

---

### Post by taurus on 2007-02-11
Can you log into a console, <Ctrl><Alt>F2, and see view your ~/.xsession-errors to see what's the problem is?

```
cat .xsession-errors
```

---

### Post by elBorba on 2007-02-11
Yes, it gives me a whole great string of error messages.

The list starts with a buch of "libGL Warning: 3D driver claims not to support visual 0x## " messgaes.

Then there are a few xscreensaver unrecognized ClientMessage entries.

Then I get a "X connection to: 0.0 broken (explicit kill or server shutdown)"

followed by a buch of messages indicating that various processes have lost their connection to the display.

---

### Post by elBorba on 2007-02-11
After some further digging through this forum, it seems that my problem is due to some known issues with the 3dfx driver for xserver.

Unfortunately I have a Voodoo3 card.

I gues I'll trty loading Dapper, apparently that does not have the same issues.

---

