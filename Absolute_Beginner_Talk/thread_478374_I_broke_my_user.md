---
title: "I broke my user"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by ditchwater on 2007-06-19
I accidentally removed myself (the only user on a ubuntu machine) from every group bar one useless one. (i unwittingly issued a sudo usermod -G command, thinking it would just add me to a group, not knowing it would remove me from every other group) and now of course the user can't do any admin, which means I can't sudo, which means I can't put myself back in the groups I need to be in to do admin. Catch 22.
Now, I have a backup copy of the /etc/group file, which I understand is the file i need to fix things, but of course I can't replace the existing etc/group without sudo.
So, what can I do? Is my best option to boot from the live disk, grab the backup group file, and overwrite /etc/group? is that all I need to do? Is there a way to fix things without booting the live CD?
I have the latest version of Ubuntu, fully up to date. It's only got the one superuser, me, that was automatically created at installation. I never got around to creating a password for root . . .

thanks a million, in advance

john

---

### Post by lazyart on 2007-06-19
If you have the backup of the group file, boot into recovery mode by hitting ESC when you see grub message and selecting recovery mode.  It will eventually dump you into the command line as root and you can do```
cp /path/to/backup/group /etc/group
```

More info here: [http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

I had this happen a couple weeks ago.  It's easy to fix.

---

### Post by w4ett on 2007-06-19
Here's the Wiki on the subject with how-to instructions:

[https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

---

