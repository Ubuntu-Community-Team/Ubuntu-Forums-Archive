---
title: "[SOLVED] Clear Saved Session"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by snkiz on 2007-09-24
Hi All, I'll Get To The Point I Managed To Crash Out Of Session But Because Ubuntu Is Set To Auto Save On Logout When I Try To Log In Again It Reloads Whatever Is Causing The Crash. I Can Get In With A Failsafe Session, So Is There A Way To Clear The Saved Session And Have My Next Log In Start Fresh?

---

### Post by mesilliac on 2007-09-25
Your session info should be stored in the $HOME/.gnome2/session file, where $HOME is your home directory. If you know which program caused the problem you can try editing this file with gedit to remove the corresponding entry.

Otherwise, just delete this file and your session will revert to the default.

---

### Post by snkiz on 2007-09-25
Thank You I've Rephrased That Question Several Times Trying To Get The Simple Solution Witch You Have Provided. Every One Else Told Me To Look For Complex Config Or Graphics Issues. Thank You Again.

---

