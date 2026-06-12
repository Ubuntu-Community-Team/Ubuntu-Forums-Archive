---
title: "Evolution Forgets Passwords"
date: 2012-08-29
forum: Any Other OS
---

### Post by ChrisNZ on 2012-08-29
Fresh Installed Mint 12, Evo 3.2.2 from Synaptic sources. Evo' will not remember passwords on open. Once passwords have been keyed in - fine. "Save password"box ticked. Multiple email accounts all but one on gmail. All on "Pop" settings.
Really bugging me - although issue is not new here on forums, have not found the answer.

Have downloaded the latest Evo thinking I could install that but it's in a .tar.xz format!

Please can you help?

---

### Post by Perfect Storm on 2012-08-29
Moved to Other OS/Distro Talk.

---

### Post by ChrisNZ on 2012-08-30
THis may now be related to the changes at login. I was logged in under the "Mate" sessions. If you select the "sproket Icon" you can change the type of sessions (Be aware this may help) So I tried the Gnome. Except I had no toobars and very little control on screen, logout/login - then I went to Gnome "Classic". This had more control and Evo actually started Ok to get email. That was a first without asking for any passwords!

Will see if this is stable and post followup after .... a week?

---

### Post by dodo3773 on 2012-08-30
Evolutuion needs gnome-keyring. That is why it actually stores your password in gnome. I use it under openbox. I used to export the settings from the keyring, now I just load it in my .xinitrc before my window manager: 
```

/usr/bin/gnome-keyring-daemon --start --components=gpg
/usr/bin/gnome-keyring-daemon --start --components=pkcs11
/usr/bin/gnome-keyring-daemon --start --components=secrets
/usr/bin/gnome-keyring-daemon --start --components=ssh

```

Here is the old way I used to do it:
```

#! /bin/bash
eval \`gnome-keyring-daemon\`
export GNOME_KEYRING_PID
export GNOME_KEYRING_SOCKET
exit


```

---

