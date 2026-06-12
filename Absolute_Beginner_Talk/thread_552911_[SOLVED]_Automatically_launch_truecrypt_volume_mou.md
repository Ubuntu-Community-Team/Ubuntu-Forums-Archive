---
title: "[SOLVED] Automatically launch truecrypt volume mount after login"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by Arthur Archnix on 2007-09-17
I've got this command I run to mount a truecrypt volume:
```
tcm --mount-options gid=100,uid=1000,umask=000 --filesystem ntfs-3g /dev/sda4 /home/arthur/Locker
```
I want to have this run at startup. That is, after I log in, I want a terminal window to pop up, prompt me for the password, yadayadayada.

Can't seem to get it to work. Tried all sorts of things. Might have something to do with the fact that I've configured truecrypt to be run by a normal user, using the commands "tc" to run truecrypt or "tcm" to mount a truecrypt volume.

It involved a gentoo forum and bash.bashrc

---

### Post by Arthur Archnix on 2007-09-18
UPDATE: So when I create a launcher with the command above, and I select that the command ought to be run in a terminal, I get the following error:

```
There was an error creating the child process for this terminal
```

---

### Post by Arthur Archnix on 2007-09-19
Ok, so I've created a script that goes as follows:
```
# /bin/sh
tcm --mount-options gid=100,uid=1000,umask=000 --filesystem ntfs-3g /dev/sda4 /home/arthur/Locker
```
When run it returns an error saying tcm is an unknown command. I've previously defined tcm in bash.bashrc (correct?) as an alias for truecrypt -m, and this works fine when run from the terminal, but for some reason when called from a script it does not.

I did this because it was the only way I could mount a tc volume as user without root privileges.

I'm open to suggestions / good sources of information.

---

### Post by justask on 2007-09-25
See this:

[http://ubuntuforums.org/showthread.php?t=527713](http://ubuntuforums.org/showthread.php?t=527713)

---

