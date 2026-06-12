---
title: "[SOLVED] odd problem related to user accounts - help!"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by kleo skywalker on 2007-07-30
Most other stuff in my newly installed Feisty seems to work ok, but there's an unexpected problem.
I have 2 user accounts, with the same privileges (which I customized through System-->Administration-->Users and groups) except that one can administer the system and the other can't.
Now from the administrator account, I installed the adobe flash player thing for mozilla firefox, and websites or pages that use flash show up as they should in this account. However, the other user - the one without administrative privileges, can't see them this way and gets the "click here to install adobe flash player" message.
I have no clue why this should be happening! Please help.

---

### Post by asmoore82 on 2007-07-30
did you install flash from inside of firefox or systemwide via apt/synaptic ??

---

### Post by kleo skywalker on 2007-08-02
From inside firefox, by clicking the missing plug-in thing.

---

### Post by kleo skywalker on 2007-08-02
So I tried installing it using aptitude, and also synaptic, but same problem each time. It downloads, but doesn't install. I get a message saying:
> md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

Why? And what do I do?

---

### Post by kleo skywalker on 2007-08-02
Oh I just had to upgrade it. It's installed now.

---

