---
title: "My Terminal doesn't work! Can someone help please?"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by fantasyspirit91 on 2007-08-16
Every time I click on Terminal, no window comes up, but there is a tab on the bottom that says, "Starting Terminal." But it disappears after a few seconds. Terminal doesn't work! How can I fix this? Thank you for your help!

Specs:
Pentium D 805
1 gig of ram
Geforce7300GS

---

### Post by heimo on 2007-08-16
> **fantasyspirit91 said:**
> Every time I click on Terminal, no window comes up, but there is a tab on the bottom that says, "Starting Terminal." But it disappears after a few seconds. Terminal doesn't work! How can I fix this? Thank you for your help!

First I'd try running xterm. Hit alt+F2, write "xterm" and hit Run. If it runs, write "gnome-terminal" on it and hit enter. Does a new gnome-terminal open? If not, is there any error messages on xterm window?

If not, open System Monitor (System->Administration->System Monitor) and try ending all "gnome-terminal" processes and try opening terminal again.

---

### Post by ThrobbingBrain66 on 2007-08-16
Hit Alt+F2 and type gnome-terminal into the box that pops up, does this open a terminal?

---

### Post by Paul133 on 2007-08-16
What happens if you do alt+F2 and then enter ```
gnome-terminal
``` in the popup box? If that doesn't work, try ```
xterm
```

---

### Post by vambo on 2007-08-16
Assuming that this is the Gnome terminal that's acting up. Have you tried Konsole
Applications -> System Tools -> Konsole

---

### Post by fantasyspirit91 on 2007-08-16
xterm works, and I'm downloading Konsole now.

However, gnome doesn't work. Is it okay that it doesn't work? Thanks again.

---

### Post by Paul133 on 2007-08-16
OK, so gnome-terminal doesn't work. Does anyone know how to fix it? I guess use Konsole until then. If Konsole doesn't work, just use xterm.

---

### Post by fantasyspirit91 on 2007-08-16
Okay, but I can't paste. Shift+Ctrl+V doesn't work. >.<

---

### Post by heimo on 2007-08-17
> **Paul133 said:**
> OK, so gnome-terminal doesn't work. Does anyone know how to fix it?

To debug what's wrong, I'd create another user account and try running gnome-terminal there. If it works, it may be configuration problem or something that's left running or locked and prevents gnome-terminal from opening. I'd probably also run it prefixed with strace and see if I can find any clues. Reinstalling gnome-terminal is unlikely to solve this, but worth trying anyway.

---

