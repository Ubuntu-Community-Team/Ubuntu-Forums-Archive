---
title: "sbackup does nothing"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by larryhowe on 2007-12-02
I installed sbackup using synaptic. I configured it according to the various online guides. When I click Backup Now!, nothing happens. That is the first problem. I also notice threads on here saying people are unable to restore files using sbackup.

1 - does anyone know how to make sbackup actually run a backup.
2 - has anyone ever successfully restored an sbackup backup.

Larry

---

### Post by skyjacker on 2007-12-02
> **larryhowe said:**
> I installed sbackup using synaptic. I configured it according to the various online guides. When I click Backup Now!, nothing happens. That is the first problem. I also notice threads on here saying people are unable to restore files using sbackup.

1 - does anyone know how to make sbackup actually run a backup.
2 - has anyone ever successfully restored an sbackup backup.

Larry
1) sbackup does its work in the background... You can't see the files as it backs them up. Go to /var/backup to see if you have a file with the date of your backup.
2) Haven't tried to restore a backup yet, as I have not needed to, but now you've got me curious.

---

### Post by larryhowe on 2007-12-02
The reason I say it does nothing is because it says it is starting a background process, but that process quickly dies. There is no /var/backup directory. Nothing is written to a log anywhere that I can find. I want to backup to a network location and there is no network activity.

A process that fails and doesn't give you any troubleshooting message or write a log anywhere reminds me of Windows.

Larry

---

### Post by mdpalow on 2007-12-02
If you like a visual confirmation your back-up is working and you don't mind moving the back-up file(s) to another location when they're (1-3 files) finished, then see link below in my signature.

I've used it to back-up & restore many times and it works perfectly...

---

### Post by larryhowe on 2007-12-02
OK, made some progress. It was making a bunch of zero-length files in the destination location (which is a NAS drive which is SMB mounted to the PC). On the Include tab, I wanted to include /, and then exclude specific directories. When I try to include / using the  GUI, it shows up as //. I went into /etc/sbackup.conf and changed // to /, like so:

[dirconfig]
/ = 1
/proc/ = 0
/media/ = 0
/data/ = 0
/var/cache/ = 0
/tmp/ = 0
/dev/ = 0
/lost+found/ = 0
/mnt/ = 0
/var/spool/ = 0
/var/tmp/ = 0
/sys/ = 0

and now it is backing up! Apparently, you can't choose / as an include path using the GUI, but you can do so by editing sbackup.conf directly.

Larry

---

