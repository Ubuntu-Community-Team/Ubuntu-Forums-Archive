---
title: "stupid mistake while moving /home- need help"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by eilu on 2006-10-29
](*,) stupid mistake while I was moving /home to its own partition... I partitioned and moved everything without a hitch, but forgot to tell ubuntu where the new /home was...

Now ubuntu keeps telling me it can't find my home folder (formerly /home/eilu; now it's in /media/newhome) and I can't log in. The only session that works is the failsafe terminal... how do I correct this?

---

### Post by taurus on 2006-10-29
Boot into recovery mode from GRUB and at the prompt, edit your /etc/fstab to point /home to new the new place...

```
nano -B /etc/fstab
```

---

### Post by John.Michael.Kane on 2006-10-29
You can try gparted which can be run from the live cd.

Or

Try editing the mount point using fstab while in failsafe

Last resort reinstall

---

### Post by eilu on 2006-10-29
tried modifying fstab so that /dev/hda4 has /home as mount point, but now Ubuntu is flashing an error message that reads:
"User's $HOME/.dmrc file is being ignored. This prevents the default session from being saved..." and something about 644 permissions... :(

I'd really like to avoid reinstalling because it takes forever to download updates and programs on dial-up... but maybe I should just remove dapper and start over with a fresh install of edgy.

---

### Post by taurus on 2006-10-29
Make sure you are the owner of that file and it has permissions of 644 or 600.  Assuming that you are still in recovery mode and your username (regular account) is john.  Do

```
cd /home/john
chown john:john .dmrc
chmod 600 .dmrc
```
Reboot and see if you can log in as john now...

---

### Post by eilu on 2006-10-29
> **taurus said:**
> Make sure you are the owner of that file and it has permissions of 644 or 600.  Assuming that you are still in recovery mode and your username (regular account) is john.  Do

```
cd /home/john
chown john:john .dmrc
chmod 600 .dmrc
```
Reboot and see if you can log in as john now...

that did the trick. thanks! Lesson learned. I'm won't be mucking around with the system in a long time. Must be more careful... :)

---

### Post by taurus on 2006-10-29
> **eilu said:**
> that did the trick. thanks! Lesson learned. I'm won't be mucking around with the system in a long time. Must be more careful... :)
Good.  Actually, if you screw up, you only hose your $HOME so you don't have to reinstall the whole system.  Just make a regular backup of your $HOME just in case and you are all set to go...

---

### Post by eilu on 2006-10-29
will do. much thanks.

---

