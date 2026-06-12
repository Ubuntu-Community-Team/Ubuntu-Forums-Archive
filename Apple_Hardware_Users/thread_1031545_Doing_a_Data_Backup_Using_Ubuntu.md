---
title: "Doing a Data Backup Using Ubuntu"
date: 2009-01-05
forum: Apple Hardware Users
---

### Post by Killtodie on 2009-01-05
I got a MacBook pro here with a LOT of bad sectors. Using the OSX discs it failes to repair or clone. It boots to the OS but freezes at the desktop so I cant do a data backup within.

I can boot to Ubuntu 8.10 but since the account is password protected I cant access or copy the data over at all.

Is there anyway around this? I tried chmod and similar.

---

### Post by Killtodie on 2009-01-05
ok, screw that. had to take the damn thing apart. now I got it hooked up to another mac. Im accessing the users folders but its taking a long time cause of all the bad sectors.

Whats the mac equivalent of chkdsk or fcsk?

---

### Post by cyberdork33 on 2009-01-05
Macs have something called "target mode" if you start it up holding 't'. This allows you to turn a mac into an external firewire drive for another computer, which you can then perform repair or backup on. Much easier than taking one apart :)

another alternative would be to boot the broken machine into single-user mode. (hold CMD+S during bootup). This starts the machine to a shell and a root login. There are direction to use the commandline repair tools there.

Now, onto Ubuntu:
Because Linux respects the file permissions on teh OSX filesystem, the files you are trying to access are "owned" by a different user than the Ubuntu LiveCD user and are not accessible. Additionally, chmod does not work properly because the file system is mounted read-only. You need to access the files with root permission.

Open two nautilus windows via gksudo:
```
gksudo nautilus
```

Then navigate one to the files to backup and one to your backup medium. Then simply drag files where you like.

OSX is UNIX, so the same filesystem checking tools are on there:
```
[FONT=Helvetica, arial][SIZE=2]/sbin/fsck -y
```

might need to do a sudo with that...[/SIZE][/FONT]

---

### Post by Killtodie on 2009-01-05
Thank you, that was very helpful.

I got the backup done in the meantime. Macbooks aint that hard to take appart, but that information will definitely be useful in the future.

---

### Post by cyberdork33 on 2009-01-05
> **Killtodie said:**
> Thank you, that was very helpful.

I got the backup done in the meantime. Macbooks aint that hard to take appart, but that information will definitely be useful in the future.
depends on which machines you are talking about :) The G3 iBooks had to be almost completely disassembled in order to replace a hard drive, the newest macbooks have a door for the hard drive.

---

### Post by Killtodie on 2009-01-05
I got 2x mac books pro 17" a powerbook G4, both easy and a iBook G4, hard

---

