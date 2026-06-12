---
title: "ctrl-alt-backspace not working"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by omrsafetyo on 2007-07-08
I seem to have broken something.. though I'm not sure how or what.  I have made changes to my xorg.conf, but only to enable composite extensions.

I first noticed that when I press the  "log-off, switch user, lock screen..." button, nothing happens.  Well, I won't say nothing - but at least nothing graphical.  It seems something is happening, and pressing esc will cause whatever is happening to quit - but I do not get the shutdown menu.

Also, the key stroke combination for kill X (ctrl+alt+backspace) doesn't work properly.  Instead of killing X, it restarts my computer.  Pretty near the only option I currently have for restarting my PC is the shutdown command from the terminal..

Does anyone have any ideas for restoring this functionalities, because I am stumped?

Thanks.

---

### Post by omrsafetyo on 2007-07-08
oh yeah... x86-64, Edgy EFT 6.10 64 bit

thanks

---

### Post by omrsafetyo on 2007-07-08
Does anyone have any ideas for this?  I'm lost.

I can still use other ctrl+alt+f[123456] to move to other tty sessions, and then return with Alt+F7 - but no luck on the Ctrl+alt+backspace

---

### Post by omrsafetyo on 2007-07-08
This problem has been solved (both symptoms).

I went into the session manager, and deselected the "Ask at log out" option.

I then clicked the Quit.. button from the system menu.

This rebooted my computer.

Upon reboot, I went back to the session manager, and reselected this - as it did not help the problem at all.  When I did this, I again tried the Quit button, and it gave me the dialog box, asking me how to quit (log out, reboot, switch user, etc.).  I hit cancel, and tried ctrl+alt+backspace - and this killed and restarted X successfully, without a powerdown/reboot.

I am not sure what caused this to hang, and may report it as a bug - but for now this problem is solved.

---

### Post by omrsafetyo on 2007-07-08
And... no sooner did I post that, and its back. :(

---

