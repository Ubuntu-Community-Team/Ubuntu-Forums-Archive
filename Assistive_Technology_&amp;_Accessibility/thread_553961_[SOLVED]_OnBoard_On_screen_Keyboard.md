---
title: "[SOLVED] OnBoard On screen Keyboard"
date: 2007-09-18
forum: Assistive Technology &amp; Accessibility
---

### Post by BSBarrows on 2007-09-18
I am trying to make a tablet out of my laptop, I have a touch screen and I am using the onboard keyboard, the only problem, when I put it to sleep, suspend it, when it returns it ask's for a password over a black screen and there is no way to open the keyboard that I know of. So if there is a way to get the keyboard so that it shows up on the wake up screen coming back from suspend, that will help me sooo much, because with out that I can't get back in after I suspend. Also if I get rid of the password prompt coming back from suspending the tablet. If anybody has a fix for this and can lay it out for me simply, I am new to Ubuntu. Thanks to anybody that can help me out.

---

### Post by BSBarrows on 2007-09-19
come on people, does anybody know what to do?

---

### Post by Leaf on 2007-09-19
In system->prefs->accessibility accessibility prefs

there is an option to show on screen keyboard at login.

You might want to check this thread [http://ubuntuforums.org/showpost.php?p=2957545&postcount=10]("http://ubuntuforums.org/showpost.php?p=2957545&postcount=10") for information on how to resize/position it so it downt completely obscure your login box.

---

### Post by BSBarrows on 2007-09-19
Yes there is a show at login button, and it does, but for some reason it doesn't show up when I try to log back in after I suspend the machine, I am trying to use this laptop as a tablet, there for it only has a touch pad, so I kinda really need this to get back from the suspend. If there is a way to get around not having a password coming back from suspend that would be even better. Thanks to anybody that can help, be it changing the suspend so I don't need a password, or the keyboard at log back in from suspension.

---

### Post by octathlon on 2007-09-19
I haven't tested this, but if you run gconf-editor, under apps>gnome-power-manager, there are checkboxes for lock_on_hibernate and lock_on_suspend.  You could try unchecking them.

---

### Post by BSBarrows on 2007-09-19
THANK YOU!! The forum has been there for all my questions so far! I am really loving Ubuntu. Un-checking the lock on suspend mode did it (duh, should have look around just a bit more) and I can just go right back to where I started, no lock at all. Just what I wanted!

Thanks sooooo much

---

### Post by Linuturk on 2008-08-05
I'd like to propose a better fix for this. 

Similar to the Accessibility options of the Login Manager, gdm, you can have an onscreen keyboard appear after you move the mouse in a special way. See: [https://help.ubuntu.com/community/Accessibility/OnboardAndMousetweaksAtGDM](https://help.ubuntu.com/community/Accessibility/OnboardAndMousetweaksAtGDM)

Why can't we have this same option on the screensaver prompt?

---

### Post by Crafty Kisses on 2008-08-30
> **BSBarrows said:**
> THANK YOU!! The forum has been there for all my questions so far! I am really loving Ubuntu. Un-checking the lock on suspend mode did it (duh, should have look around just a bit more) and I can just go right back to where I started, no lock at all. Just what I wanted!

Thanks sooooo much

Mark the thread solved.

---

### Post by aflores on 2009-10-30
I'm not sure if this really qualifies as solved.  I want to have a login screen after suspend, but I would like to be able to use the onscreen keyboard.  Is it possible to have the same login screen (with the onscreen keyboard) after you resume from suspend?

---

### Post by GroovingClockwork on 2010-07-09
Having the same issue as the original poster, I just found out that if you install onBoard virtual keyboard, then in the Settings window there is an option "Show onboard when unlocking the screen". Perfect - security and accessibility at once.

This may be absent on older versions though: cf. [https://answers.launchpad.net/onboard/+question/65940](https://answers.launchpad.net/onboard/+question/65940)

---

