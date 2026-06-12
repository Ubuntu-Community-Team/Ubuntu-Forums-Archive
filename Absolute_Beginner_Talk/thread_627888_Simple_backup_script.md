---
title: "Simple backup script"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by Sutur on 2007-11-30
Just need some help making this work properly.

It's function is to restore permissions and backup my system:

```
#!/bin/bash
gksudo "mount /dev/sdc1 /media/sata_02 -t reiserfs" &&
gksudo "chmod 755 /media/sata_01 -Rv" &&
gksudo "chmod 700 /media/sata_01/Misc/Private -Rv" &&
gksudo "rsync -ar --delete-after --ignore-existing --progress /media/sata_01/ /media/sata_02/" &&
gksudo "umount /dev/sdc1"
```

I have created a button on my panel so that I can perform a backup whenever anything changes, if I add new files and folders or remove them:

**Type:** Application in Terminal
**Name:** Backup to SATA 02
**Command:** gksudo "/home/sutur/misc/txt/backup"



The problem I have, is that the script won't stay in a terminal and report verbose data. It just opens the terminal, quickly closes it, and stops.

Second problem is that /dev/sdc1mounts during bootup even though I have hashed it out from /etc/fstab.

Help appreciated.

---

### Post by vikram on 2007-11-30
you can either pipe the output of each command to a file with a > filename.log at the end

eg.

ls > lsoutput.log

or add this to the script

$ read -p "Press any key to end"

this will wait for user input before closing the screen

---

### Post by Taboo Mirage on 2007-11-30
Why not output stdout and stderr to a logfile?  Put something like this at the top:

```
logfile=/var/log/script.log

exec 1>>$logfile
exec 2>>$logfile
```

Also, why not take all of those "gksudo" commands out too?  For one thing, "gksudo" is only meant to be used for executing graphical applications which require root permissions.  Secondly, it'd just be easier if you ensure that the script itself is being executed as a root user.

```
if [ $(whoami) != "root" ]; then
	echo "Please ensure you're executing this script as root!"
	exit 1
fi
```

You could then run the script with:

```
sudo /path/to/script
```

These snippets were written quickly by me as a demonstration.  I recommend looking up the methods I've used and adapt them to suit your needs.  If you redirect the outputs before checking if you're running the script as root, obviously the error message will not be displayed in the terminal therefore I recommend adapting the code I've provided to execute the redirections in an else statement after the check.

Take care.

---

### Post by Sutur on 2007-11-30
Thanks people I have got it to work.

Removing gksudo and the inverted commas seems to have done the trick, strangely enough.

The terminal stays and reports the data verbosely - exactly what I wanted.

Still the problem of that persistent /dev/sdc1 mounting even though it's been hashed, any ideas on this one?

---

### Post by Sutur on 2007-12-02
Bump for help on automount.

I did some research and discovered that the HAL daemon can have policies/rules.

After reading [this]("http://wiki.archlinux.org/index.php/HAL#Auto-mount_only_removable_media"), I discovered I could fix my problem. But even after adding this rule a shortcut to /dev/sdc1 still exists in the Thunar places sidebar. True to the rule, this partition is NOT mounted at bootup, but if you click on the link it requests the password and mounts it.

Can't I remove the link altogether and have /dev/sdc1 fully manual?

---

