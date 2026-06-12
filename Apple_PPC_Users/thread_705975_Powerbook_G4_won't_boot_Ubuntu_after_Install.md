---
title: "Powerbook G4 won't boot Ubuntu after Install"
date: 2008-02-23
forum: Apple PPC Users
---

### Post by powerbookluv111 on 2008-02-23
Hello. I just installed Ubuntu 7.10 on my Powerbook G4 667mhz. I formatted and used the entire drive. When I turn  on the computer, I get the boot screen and hit 'l' It loads a comple of screens and then stops at a black screen with a white non-blinking cursor in the upper left hand corner. What is this, and how do I get past it? There were no errors generated during Ubuntu installation. No errors at all. Please help! I seriously want Ubuntu.

---

### Post by stream303 on 2008-02-24
You may have to use
video=ofonly

at the boot:  prompt.

Check these faqs out and let us know how it goes:

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

---

### Post by powerbookluv111 on 2008-02-24
Already use:
live-nosplash-powerpc video=ofonly break=top

In order to get it to boot past a messed up visual affect. I get the same result using the alternate install or the live cd.

I've read that you need to edit /etc/initramfs-tools/modules and add: ide_core at the end. But, how do I edit /etc/initramfs-tools/modules, because I can never get to a terminal. Or should I boot the live CD, and edit it through there?

---

### Post by powerbookluv111 on 2008-02-24
Let be more clear. I used those to boot the Live CD. Are you talking use video=ofonly to boot the installed linux? I just tried and couldn't get that to work either.

---

### Post by stream303 on 2008-02-24
> **powerbookluv111 said:**
> In order to get it to boot past a messed up visual affect. I get the same result using the alternate install or the live cd.

The Ubuntu splash screen never looks right, even on good installs so don't sweat that too much.

> I've read that you need to edit /etc/initramfs-tools/modules and add: ide_core at the end. But, how do I edit /etc/initramfs-tools/modules, because I can never get to a terminal. Or should I boot the live CD, and edit it through there?

If your live-cd is usable, at least temporarily, I'd fire up the terminal and see if ide-core is in that directory already.  NOTE:  I see you used an underscore, use a **hyphen** instead: **ide-core**

If you need to add it, you can do ALT-F2 (no ctrl key) to bring up a gui window which will allow you to get into the editor as root to do your editing, ala

```
gksudo gedit /etc/initramfs-tools/modules
```

or you can start this the same way from the gui terminal: gksudo gedit .....

---

### Post by powerbookluv111 on 2008-02-24
A hyphen! Wherever I found that had an underscore. If i entered that for the install, could that lead to all of these problems? I wouldn't have thought so, but I don't know. Thanks for you help, I'll have to reinstall it here now, I needed my latpop back, so I reloaded OS X. But I'll try.

---

### Post by stream303 on 2008-02-25
I saw that underscore too, but I remember seeing it being corrected with a hyphen, and the PPC KnownIssues page shows it as a hyphen:

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

Even though you reinstalled OSX, if you feel like doing it again,  you could partition your drive in half for example, and have a dual boot setup.

---

### Post by powerbookluv111 on 2008-02-25
Which is what I originally attempted to do, but thought maybe it would just be better to wipe the drive, after it failed a couple of times. Do you also have any idea why "Select and Install Software" would fail using the alternate install CD? That was the only problem with that.

---

### Post by stream303 on 2008-02-25
Hm... how about giving Feisty 7.04 alternate a try?  Then maybe later do an in-place upgrade.  It might be a bit easier..

---

