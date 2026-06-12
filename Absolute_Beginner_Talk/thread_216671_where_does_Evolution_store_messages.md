---
title: "where does Evolution store messages?"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by slowcanuk on 2006-07-15
having a nice working system I "improved" my video card and messed up the ATI driver configuration. Rather than fighting, I would like to backup my saved messages and do a complete reinstall. I know I saved about 30Mb of messages, 25M are high res falcon pictures, but I could not find anything this size in the home/username/.evolution directory nor the var/mail directory.
J.

---

### Post by FilthyLiar on 2006-07-15
[http://ubuntu.wordpress.com/2005/12/03/how-to-backup-evolution/](http://ubuntu.wordpress.com/2005/12/03/how-to-backup-evolution/)

> "From an old mailing list gem, I got the right method to back up your Evolution (mail + calendar + contacts) data the right way:

Step 1:
Shutdown evolution and gconftool-2:
```
$ gconftool-2 --shutdown
$evolution --force-shutdown
```

Step 2:
Create an archive with the data and configuration files:
Note: To completely save the Evolution data and configuration, you need to save the following directories/files:

   1. ~/.evolution/
   2. ~/.gconf/apps/evolution/
   3. ~/.gnome2_private/Evolution

The following command will take care of these
```
$cd
$tar -cvzf evolution-backup.tar.gz .evolution .gconf/apps/evolution .gnome2_private/Evolution
```

Now the file evolution-backup.tar.gz is the backup you want. You can move the data over to another Ubuntu computer if you like, and just un-tar the archive while in your /home/username/ directory to restore it."

---

### Post by slowcanuk on 2006-07-15
thank you for finding the post I could not, now to boot with a live CD, create the tar.gz and save to a USB stick.
wish I could use the working windows partition to do this but it has issues with file names and of course directory names <sigh>
J.

---

### Post by slowcanuk on 2006-07-17
> **slowcanuk said:**
> thank you for finding the post I could not, now to boot with a live CD, create the tar.gz and save to a USB stick.
wish I could use the working windows partition to do this but it has issues with file names and of course directory names <sigh>
J.

OK, because the Ubuntu system seemed unbootable because of the messed up ATI setup I booted with a Knoppix live CD and cd'd to MY home directory and typed
knoppix@1(my user name)$ tar -cvzf evolution-backup.tar.gz .evolution .gconf/apps/evolution .gnome2_private/Evolution and got the error message 
tar evolution-backup.tar.gz: Cannot open Read-only file system...

so using a usb stick, which was in fact /mnt/sda1 I changed the command to 
knoppix@1(my user name)$ tar -cvzf /mnt/sda1/evolution-backup.tar.gz .evolution .gconf/apps/evolution .gnome2_private/Evolution and it of course worked. 
Hope this helps someone else save files when the live CD mounts the hard drive as read only.

---

