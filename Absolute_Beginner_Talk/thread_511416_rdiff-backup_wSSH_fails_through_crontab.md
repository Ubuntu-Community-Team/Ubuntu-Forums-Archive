---
title: "rdiff-backup w/SSH fails through crontab"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by Acksys on 2007-07-27
Hi all,

I recently used the steps from [http://arctic.org/~dean/rdiff-backup/unattended.html](http://arctic.org/~dean/rdiff-backup/unattended.html) to setup a backup server to pull a nightly rdiff-backup of my laptop's installation over SSH. Everything worked  great until I tried to put the job in my crontab.

I set up a user called rdiff-backup with shell /bin/false to do this backup, per the instructions in the above article.

If I su to this user to perform the backup manually , it runs fine.

```

sudo
su -m rdiff-backup
rdiff-backup --exclude /mnt --exclude /tmp --exclude /proc --exclude /media --exclude /sys --exclude /lost+found fishie-backup::/ /media/sda3/backup/laptop-backup

rdiff-backup@acksys-studio:/var/log$ rdiff-backup -l /media/sda3/backup/laptop-backup

Found 2 increments:
  increments.2007-07-23T00:15:50-04:00.dir  Mon Jul 23 00:15:50 2007
  increments.2007-07-26T17:11:09-04:00.dir  Thu Jul 26 17:11:09 2007
Current mirror: Fri Jul 27 18:16:48 2007 
```

However, when I add it to rdiff's crontab

```

crontab -e -u rdiff-backup

# m h  dom mon dow  command
30 6 * * * rdiff-backup --exclude /mnt --exclude /tmp --exclude /proc --exclude /media --exclude /sys --exclude /lost+found fishie-backup::/ /media/sda3/backup/laptop-backup

```

and come back the next day, I get an error saying rdiff-backup "seems to have failed" when I check the backup with rdiff-backup -l. When I run it again manually, it regresses the destination and backs up again, seemingly successfully (albeit with some innocuous-looking errors about special files).

Any ideas what could be causing this? /var/log/syslog.0 shows the cron job running on the backup server, and I don't see any obvious clues in any of the logs on either machine.

---

### Post by Acksys on 2007-07-28
Bump! Is there a more appropriate forum to ask this question? I'd appreciate any help.

---

