---
title: "add script to panel (with feedback)"
date: 2005-07-05
forum: Absolute Beginner Talk
---

### Post by secundar on 2005-07-05
I use rsync to backup a few files from my laptop to another computer. i've added the following to sync.sh and made it executable - it seems to work but i would like a terminal window to remain open so i can view the progress of the script - so i know if and when it completes...

```
#!/bin/bash

# Backup important stuff. List of directories are rea from backup_list

# TODO: Alter script so terminal window remains open after rsync so that stats can be read

rsync -arvz --progress --files-from=/mnt/shared/backup_list /mnt/shared gary@192.168.2.29:/home/gary/backups/
```

---

