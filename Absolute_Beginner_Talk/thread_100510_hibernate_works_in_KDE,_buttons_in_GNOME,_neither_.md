---
title: "hibernate works in KDE, buttons in GNOME, neither vice-versa?"
date: 2005-12-07
forum: Absolute Beginner Talk
---

### Post by vettejock99 on 2005-12-07
Hello all,

I am learning Linux through a lot of research and trial and error, and I've had some success getting it working on my laptop with WPA, etc. in the past.  However, I am trying Ubuntu 5.10 now, and it is appealing, especially as suspend to ram works on my HP laptop when I use KDE and the volume and mute buttons on my laptop work when I am using GNOME.  However, these functions do not work in the other window manager (so, no volume/mute button capability in KDE at this time).

I did an lsmod, and it didn't tell me much (at least that I could see) about what my problem might be.  I thought maybe somebody here could confirm for me that it has something to do with the applets or scripts built in to each session manager, and if I can easily enable both functions in each manager by looking at a configuration somewhere.....

Thanks for any help!

---

### Post by Estariel on 2005-12-07
in KDE: try launching khotkeys (from the konsole, from system settings or from "alt+F2").
If you are lucky, you can just assign a function to the multimedia keys...
If you are not lucky, post again :)

---

### Post by ltmon on 2005-12-07
I can probably help with your multimedia keys.

There will be a hidden file in your home directory called ".Xmodmap" (no quotes).  On startup gnome will load this file in order to map your special key functions to keystrokes that can be understood by the Xorg.

KDE does not automatically load this file.  To make it do so you need to put a link to a script inside your ~/.kde/Autostart directory.

The script would be something like:

```

#!/bin/bash
xmodmap ~/.Xmodmap

```

Make the script exectuable ("chmod +x script.sh") and next time you log in the keys will be available.

At this stage at least the volume up and down should be working.

Note that this does not assign shortcuts to any of your keys, it just makes the keys *available* to be shortcutted.  To actually assign shortcuts you should either do as the previous poster suggested, or in an individual program there will be a menu item (90% of the time) saying "Configure Global Shortcuts...".  The "Configure Shortcuts..." menu item is useful also for things like web browser back and forward - you want this shortcut to only work when the browser is open, not all the time.

Hope this helps.

L.

---

### Post by vettejock99 on 2005-12-08
Hmm.....didn't work, but again, I am not lucky....any other thoughts?

[QUOTE=Estariel]in KDE: try launching khotkeys (from the konsole, from system settings or from "alt+F2").
If you are lucky, you can just assign a function to the multimedia keys...
If you are not lucky, post again :)[/QUOTE]

---

### Post by vettejock99 on 2005-12-08
I don't see this file in my home directory when I ls -al, but the module is there because I can type xmodmap.....how can I create it?

[QUOTE=ltmon]I can probably help with your multimedia keys.

There will be a hidden file in your home directory called ".Xmodmap" (no quotes).  On startup gnome will load this file in order to map your special key functions to keystrokes that can be understood by the Xorg.

KDE does not automatically load this file.  To make it do so you need to put a link to a script inside your ~/.kde/Autostart directory.

The script would be something like:

```

#!/bin/bash
xmodmap ~/.Xmodmap

```

Make the script exectuable ("chmod +x script.sh") and next time you log in the keys will be available.

At this stage at least the volume up and down should be working.

Note that this does not assign shortcuts to any of your keys, it just makes the keys *available* to be shortcutted.  To actually assign shortcuts you should either do as the previous poster suggested, or in an individual program there will be a menu item (90% of the time) saying "Configure Global Shortcuts...".  The "Configure Shortcuts..." menu item is useful also for things like web browser back and forward - you want this shortcut to only work when the browser is open, not all the time.

Hope this helps.

L.[/QUOTE]

---

