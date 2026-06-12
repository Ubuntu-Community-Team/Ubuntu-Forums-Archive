---
title: "[SOLVED] Problem with WIde-screen Resolutions..."
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by The Catalyst on 2007-09-08
Hi, I have an nVidia GeForce 6200 on Ubuntu, and I'm currently at 1440x900, the resolution I desire.

I downloaded Envy, it found my drivers just fine and installed them.  However, when I restart, my resolution resets back to 1280x1024 (not wide-screen - blurry)

The nVidia XServer Settings panel has a button that says "Save this configuration to xconf" or some such nonsense - I *know* this is what I need to do.  However, when I click it, it gives me the error: "Unable to remove old X Config backup file '/etc/X11/xorg.conf.backup'."

Should I just delete the old backup file?  I'm very weary about deleting files in Linux because I don't know a lot about it's inner workings...

Any help would be appriciated.

---

### Post by _mOrgoth_ on 2007-09-08
Go System, Preferences,  Screen Resolution and set it there. That resolved same problem to me.

---

### Post by alienexplorers on 2007-09-08
Try using:
> sudo nvidia-settings
you should be able to set the mode from there.

You could also add a modeline with your monitor resolution and refresh rate to you "MONITOR" section of your xorg.conf.

---

### Post by The Catalyst on 2007-09-08
Hmm, interesting results.

FIrstly, it doesn't even allow the 1440x900 display in the Ubuntu Resolution screen until I first set it to 1440x900 in the nVidia Settings screen.

Secondly, I opened the Screen Resolution Preferences window of Ubuntu and it was already set to 1440x900 so I clicked "Apply" and restarted... with no luck.  Same results as before.

Thanks for trying though, but I fear I'm suffering a different problem than you were.

---

### Post by alienexplorers on 2007-09-08
Did you try adding the modeline like I stated above.  This should lock in your resolution and refresh values.  The modeline maker can be found in my signature line.

---

### Post by The Catalyst on 2007-09-08
> **alienexplorers said:**
> Did you try adding the modeline like I stated above.  This should lock in your resolution and refresh values.  The modeline maker can be found in my signature line.

Yeah, I was typing as you posted that - a simple sudo fixed the problem, thanks :)

Sorry I'm so oblivious to the obvious, I'm somewhat new to Linux, especially a distro without an easily-accessible Root.

Thanks again guys.

---

