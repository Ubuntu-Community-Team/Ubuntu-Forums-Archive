---
title: "How can I mount a CDROM/DVD differently?"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by johann_p on 2007-12-18
When I insert a CDROM, it gets "magically" mounted under "/media/cdrom0" and its files are automatically owned by root and in mtab, the noexec flag is set.

Thats very bad, because that way I am unable to install a programm that is on CDROM and needs to noexec flag NOT to be set and needs the files to be owned by my user.

So how can I influence how Ubuntu does that autmatic mount?

When I click "Preferences" on the icon shown on the desktop for the mounted cd, there is a tab "volume" which lets me enter settings, but entering something there seems to have no effect whatsoever (yes I have ejected and remounted the CD after I have entered those settings).

The problem is that when the CD gets mounted the way Ubuntu mounts it by default, the install shell script outputs
"bash: /media/cdrom0/install: /bin/sh: bad interpreter: Permission denied"

I have googled and it seems this is because the file system from which the shell script is run has the noexec flag set.

---

### Post by diatribe on 2007-12-18
if you stop hal the cd will not automount

---

### Post by Gen2ly on 2007-12-18
This is a program for Linux?  Even if this is a program that one wants to run under wine, I think it's best to use sudo to install it.  In gnome-termial try running the script with ./ preceding it.  If this is a windows game, then "sudo wine /media/cdrom0/install" will do the job.

---

### Post by johann_p on 2007-12-18
> **diatribe said:**
> if you stop hal the cd will not automount

I would have been looking for a more general solution of how to reconfigure things so that the automounter mounts with exec instead of noexec.

I really dont want Ubuntu to take the right of me to run a program from the CD.

---

### Post by johann_p on 2007-12-18
> **Dirk.R.Gently said:**
> This is a program for Linux?  Even if this is a program that one wants to run under wine, I think it's best to use sudo to install it.  In gnome-termial try running the script with ./ preceding it.  If this is a windows game, then "sudo wine /media/cdrom0/install" will do the job.


Its a native Linux program (MATLAB). I explicitly do not want to use sudo as I want to install it in my user directory and not touch system directories. Nothing will go into any root-protected directory. 

The problem is that Ubuntu does not want to let me run a program from the CDROM file system and I want to tell Ubuntu to let me do it.

But how?

---

