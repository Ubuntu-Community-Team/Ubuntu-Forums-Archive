---
title: "Startup message"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by squrl on 2006-12-09
I am getting the long winded message on startup. I must have screwed up something. Can someone tell me how to get off the merry go round please.

Users $ HOME /.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. Users $ HOME directory must be owned by user and not writable by other users.

Thats it. I think I understand it but don't know what to do about it or how to do it.

Thanks

---

### Post by lloyd_b on 2006-12-09
Last time I saw a thread on this one, we had the user "sudo rm .dmrc" in a terminal window, and the next time it booted up everything was fine...

You might want to "cp .dmrc dmrc.bak" to save a backup first.  That way if the "delete it and let the system recreate it" method fails, you can put it back.

Lloyd B.

---

### Post by squrl on 2006-12-09
I tried it and then rebooted. Same old message. I have been tempted to put in the iso disk and start over. It would help if I had a clue as to what I was doing.

---

