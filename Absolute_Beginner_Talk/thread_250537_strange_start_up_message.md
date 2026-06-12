---
title: "strange start up message"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by EddieA on 2006-09-04
After installing an update and rebooting I got a message (after I input my password - before the desktop started up)
which said
'user /home/drmc ignored  .. should have 644 permissions.. only user should be able to write to this' etc
(if the exact wording is important I'll note it next login)

Can anyone tell me what this means and what to do about it? :confused:

---

### Post by kidders on 2006-09-04
It seems to suggest that someone on your system is called "drmc" and that he's screwed up the permissions of his home directory.

It's standard practice to lock everyone but the user himself out of his own home directory. Doing otherwise is a serious security risk, hence the warning. You should be able to fix this with:

```

sudo chown drmc:drmc ~drmc
sudo chmod 751 ~drmc

```

This will reset ownership of drmc's home, grant him full access and grant others access only to stuff *within* its directory structure that they are explicitly allowed to.

---

### Post by EddieA on 2006-09-04
Thank you for your help - I think (hope) I have solved the problem.
The full messsage was this:

"User's &HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's &HOME directory must be owned by user and not writable by other users."

The user referred to was me.
I must have changed the write permissions somehow (don't remember doing it)
Still don't know about the '644 permisions' but my machine booted Ok and the message didn't come back after I undid the write permissions.

---

### Post by kidders on 2006-09-04
Actually, now that I see the full message, I was on the wrong track, but if it's gone away, all's well that ends well, eh? :P

---

