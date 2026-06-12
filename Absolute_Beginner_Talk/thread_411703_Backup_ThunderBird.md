---
title: "Backup ThunderBird"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by delphiguy on 2007-04-17
Cheers,

I'm trying to find a way to easily backup and restore my email in ThunderBird can anyone point me in the 
right direction?

Also I have mails in OutLook and KMail is there a way for me to import them to ThunderBird?

Thanks.

---

### Post by Paul41 on 2007-04-17
I think that the Thunderbird settings and emails are stored in ~/.mozilla-thunderbird. I am at a different computer so I can't check right now, but I think you could just backup that folder.

---

### Post by seetho on 2007-04-17
Evrything is stored under the ~/.mozilla-thunderbird directory (in your home directory).  This is normally hidden.  You can see it under Nautilus by setting View->'Show Hidden Files', or do ls -a in terminal.

Just make a copy of this entire directory.  It contains all your mailboxes (in plain text files) and everything else.  To restore it to a new system, just install Thunderbird fresh; remove the newly create ~/.mozilla-thunderbird and copy in your backup.  Open Thunderbird and you will see that everything works as before.

Incidently I had to do this just last night when by system crashed.  Good thing I had a backup.

---

### Post by seetho on 2007-04-17
If you want to make a convenient backup archive your can use tar:

sudo tar -cvpzf mail-backup.tgz /home/xxx/.mozilla-thunderbird

xxx is of course your login name.

---

### Post by delphiguy on 2007-04-18
Thank you very much for all the reply.

---

### Post by vanadium on 2007-04-18
Instead of tarring, I prefer to use rsync, especially as large external UBS disks go cheep these days.

```
rsync -avq --del /home/user/.mozilla-thunderbird/ /media/USB_Data/.mozilla-thunderbird/
```

(I switched to evolution though two days ago)

Replace the left path with your actual path to the .mozilla-thunderbird folder and the right path with the path to your USB drive. There are various ways to find that path. One is: open a command prompt and type df. The output looks like:

```

~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             73939452  29093868  41089592  42% /
varrun                  517784        80    517704   1% /var/run
varlock                 517784         0    517784   0% /var/lock
procbususb               10240       128     10112   2% /proc/bus/usb
udev                     10240       128     10112   2% /dev
devshm                  517784         0    517784   0% /dev/shm
lrm                     517784     17580    500204   4% /lib/modules/2.6.17-11-generic/volatile
/dev/sdb1               999552    270064    729488  28% /media/USB
f
```

I plugged my USB stick in and on the last line, you see it is mounted on /media/USB

Using rsync has some advantaged over the tar approach:

* This command creates a copy of your data in uncompressed, readily accessible form
* This command only copies the files from the origin that have changed. Updates therefore are lightning fast: only the files that changed are copied.
* The "-del" switch deletes files in the backup that do not anymore exist in the origin, cleaning up the copy as you clean up the origin. This way, the backup each time becomes an exact copy ("mirror") of the source data. A word of caution: this can be quite dangerous: if the destination contains no files yet and you mistakenly swap source and destination, then your source files will all be deleted! Therefore, use this in a script and add the -del switch when you are sure the command is working in the right direction.

Making a script is as simple as making a text file with the command in it. Better yet, add "#!/bin/bash" as the first line to tell the system that this is a bash script. Then, make the text file executable by right-clicking, properties, permissions. If the text file is called "backup_thunderbird" then you can execute the script typing 

./backup_thunderbird

if the file resides in your current directory. Alternatively, you need to provide the pathname, eg.

~/backup/backup_thunderbird

(my backup scripts are in a directory "backup" under my home directory (~)

---

