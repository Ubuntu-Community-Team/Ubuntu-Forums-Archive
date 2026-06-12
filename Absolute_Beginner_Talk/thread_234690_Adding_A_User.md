---
title: "Adding A User"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by CeeDub on 2006-08-11
Adding a user is simple enough.  I can handle it.  But what I want is a user with the exact same profile as mine.  Can I somehow copy that over?  If so how?

---

### Post by lemonsCC on 2006-08-11
I asked this earlier:

> 
3)when setting up this box I would like all the users (except 1) to be identical (appearence, permissions, plugins, etc) is it possible to do this?

> 3- Yes, just copy the home directory of one user (for instance doing rsync) and transfer it to the home of the other user. You can use partimage as well to make exact partitions of the home directory.

---

### Post by CeeDub on 2006-08-11
Thanks for the help.  I'm just a little confused on how to use rsync.  I've tried it, but it says "skipping non-regular file"  I don't know what this means, if it's working or what.  Any more help?

---

### Post by aysiu on 2006-08-11
I think it's a bit dangerous to copy over everything. I usually just copy the appropriate folders.

If you want email and web profiles, for example, copy those. I use Thunderbird and Firefox, so I'd copy the /home/username/.mozilla and /home/username/.thunderbird directories (/home/username is also ~/)

If you're using Gnome, you'd copy over
~/.gconf
~/.gconfd
~/.gnome2
~/.gnome
~/.metacity
~/.nautilus
~/.icons
~/.themes

If you're using KDE, you'd copy over
~/.kde

Don't forget to change ownership of the newly copied files, too: ```
sudo chown -R newuser:newuser /home/newuser
```

---

### Post by lemonsCC on 2006-08-11
what should be copied in XCFE?

---

### Post by aysiu on 2006-08-12
I believe it's either ~/.xfce4 or ~/.xfce

XFCE also has some files in ~/.config

---

### Post by lemonsCC on 2006-08-12
what about .gconf .gconfd .gnome2?

---

### Post by aysiu on 2006-08-12
> **lemonsCC said:**
> what about .gconf .gconfd .gnome2?
I don't believe those have to do with XFCE... but you can try them out.

---

### Post by lemonsCC on 2006-08-12
i had no luck copying those files in the home folder.   not sure why

---

### Post by aysiu on 2006-08-12
You haven't tried something like this? ```
sudo cp -R /home/username1/.config /home/username2/.config
sudo chown -R username2:username2 /home/username2
``` If so, what errors did you encounter? What makes you think it didn't work?

---

