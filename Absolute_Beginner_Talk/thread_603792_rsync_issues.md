---
title: "rsync issues"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by phoenix24x on 2007-11-05
greetings, 

i am fairly new to linux and am currently running ubuntu 7.04. i am tryin to get backups going. i thought i had everything set up correctly but when i ran:

```
sudo rsync --verbose --progress --stats --compress --rsh=/usr/local/bin/ssh 
--recursive --times --perms --links --delete \ --exclude /proc /lost+found /mnt /sys \

```

it didnt put any files where i had thought they would be (rsyncd.conf will be at the end of post). i basically have two questions:
[LIST=1]
[*]i know rsync created a backup when i ran it but i cant find it...i dont even know the name of the backup..how do i find it?
[*]i have the rsync path (where backup is supposed to live) to /media/sdb1, which is the 2nd HDD, is that right or should it be /dev/sdb1?
[/LIST]

```
# sample rsyncd.conf configuration file

# GLOBAL OPTIONS

motd file=/etc/motd
log file=/var/log/rsyncd.log
# for pid file, do not use /var/run/rsync.pid if
# you are going to run rsync out of the init.d script.
pid file=/var/run/rsyncd.pid
#syslog facility=daemon
#socket options=

# MODULE OPTIONS

[ftp]

        comment = backing up data to the secondary HDD of ntugs20
        path = /media/sdb1
        use chroot = yes
#       max connections=10
        lock file = /var/lock/rsyncd
# the default for read only is yes...
        read only = yes
        list = yes
        uid = nobody
        gid = nogroup
#       exclude =
#       exclude from =
#       include =
#       include from =
        auth users = noneya
        secrets file = /etc/rsyncd.secrets
        strict modes = yes
#       hosts allow =
#       hosts deny =
        ignore errors = no
        ignore nonreadable = yes
        transfer logging = no
#       log format = %t: host %h (%a) %o %f (%l bytes). Total %b bytes.
        timeout = 600
        refuse options = checksum dry-run
        dont compress = *.gz *.tgz *.zip *.z *.rpm *.deb *.iso *.bz2 *.tbz
~

```

---

### Post by kebes on 2007-11-06
I don't think you're using rsync's commandline options properly. In particular, you don't specify the backup location editing "rsyncd.conf"... you specify it as an argument for rsync.

The usage is supposed to be "rsync SRC DEST" where SRC is the source of the copy and DEST is the destination of the copy (the "backup location" if you prefer). In the example you wrote, I guess you intended "--exclude /proc /lost+found /mnt /sys" to exclude those directories (proc, lost+found, etc.). But you're supposed to use it like " --exclude='/blah/' " if you want to exclude directory "blah" (you can also match patterns instead of specific directories). The way you've written it, rsync is probably trying to copy from "/proc" into "/mnt" or whatever (actually I thought it would produce an error)...


I think what you want is more like:
```
sudo rsync --archive --delete --verbose --progress --stats --exclude='/proc' --exclude='/lost+found' --exclude='/mnt' --exclude='/sys' --exclude='/media/sdb1' / /media/sdb1/backupdir/ 
```
This will try to copy everything from "/" into the directory "/media/sdb1/backupdir/" (Note that "--archive" automatically engages recursive mode and preserves timestamps, ownership, etc.)

I noticed you used "--compress" which doesn't seem necessary for a local copy. If you want to create a backup that is a single file, with everything compressed into it, then the command you actually want is "tar" not "rsync." Rsync is great for doing copy operations from one place to another (especially over the network), and is thus great for backups... but it doesn't compress the backup data.


Note that there are also plenty of GUI-based backup solutions in Linux, if you prefer (most of them use tar and rsync behind the scenes). If you're interested you can check out the recommendations in this Linux Journal article:
[http://www.linuxjournal.com/article/8931](http://www.linuxjournal.com/article/8931)


I hope that helps. If you have any other questions, feel free to ask!

---

### Post by hyper_ch on 2007-11-06
The backslash "\" is only used if you want to split the command up onto multiple lines and then the next line has to be indented (by a tab).

```

sudo rsync --verbose --progress --stats --compress --rsh=/usr/local/bin/ssh \
          --recursive --times --perms --links --delete \
          --exclude-from='/path/to/exclude_file' \
          / \
          /media/sdb1/backupdir/

```

And I would use a file that contains all excludes.

I have made - a long time ago - a small howto on how to use rsync for incremental snapshot-style backups. You'll also see the rsync command used there: [http://www.howtoforge.com/rsync_incremental_snapshot_backups](http://www.howtoforge.com/rsync_incremental_snapshot_backups)

---

