---
title: "Reverting back to Ubuntu 6.06"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2007-02-13
Is it possible to revert back to Ubuntu Dapper Drake 6.06 ..... from Edgy 6.10 without loosing the personal data stored on the hard drive?

---

### Post by etank on 2007-02-13
It depends on how you are partitioned I think. It is a good idea to set up a seperate /home partition during the install. Take a look at this [http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome). 

As far as reverting, it will probably be easier to reinstall.

---

### Post by jpeddicord on 2007-02-13
You cannot revert too easily. You will have to back up your personal data onto a CD or USB drive. I suggest backing up these folders in addition to your documents:[LIST]
[*]~/.gnome
[*]~/.gnome2
[*]~/.gaim
[*]~/.mozilla
[/LIST]They are all hidden folders, so you may want to show hidden files first (View menu in Nautilus).

Once you are backed up, wipe your Ubuntu partition clean. Install 6.06 from CD, using the same options you used for 6.10 (or change them if you want). Place your files back into the home directory (you might have to do this in recovery mode to prevent GNOME from changing them). Restart X, and the settings will be reloaded.

They should work correctly, I know from personal experience. :)

---

### Post by a.v.l on 2007-02-13
Thanks for your help.

---

