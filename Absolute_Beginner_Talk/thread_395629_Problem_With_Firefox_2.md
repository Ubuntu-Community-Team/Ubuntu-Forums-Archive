---
title: "Problem With Firefox 2"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by tm0054 on 2007-03-28
Every time I start Firefox right after a fresh boot I get the message 'Firefox was unexpectedly shut down.', with the option of starting a new session or restoring the old one, even though it was shut down properly. This message happens the first time I start Firefox on a fresh boot. I'm using Ubuntu Edgy 6.10.

Anyone have any ideas as to what could be causing this?

---

### Post by igknighted on 2007-03-28
Your saved session is probably one where FF was open.  Try at the login screen going to sessions and choosing "gnome" and not default.

---

### Post by NicoleM on 2007-03-28
are you saying you shut the computer down properly or closed firefox before shutting down and are still receiving the message?

I wasn't clear on that point, but just in case, that firefox feature is designed to be triggered any time firefox itself is not shut down by a quit, close, or exit command, etc. (note: foree quit falls into the next category which does trigger this feature)

even if you shut down or reboot your computer properly if the system has to shutdown firefox and you haven't done it manually, you will get that message.  same goes for a force quit of the program.

If it is in fact working as intended and you just don't like it, I believe this can be configured in firefox's options to not save sessions for this purpose.  there may or may not be extensions to fine tune these settings even more if you want greater control over when it happens, but i'm not sure about that, and it would be a long shot.

---

