---
title: "[SOLVED] Backup time"
date: 2008-02-21
forum: Arch and derivatives
---

### Post by bwtranch on 2008-02-21
Well, the system looks pretty good and its time  to think  about backup. I've always used tar before with the --exclude dir switch. Then just upload to my server. I have an encrypted file there were I store all my backups. Do you think I should continue to use tar or is there a better way to do this in Arch? Thank you and please surf safely.

---

### Post by BobHur on 2008-02-22
"sbackup" is a pretty simple and neat backup utility. I don't know that it does anything that you can't do with "tar", but it's handy.

---

### Post by qpieus on 2008-02-22
I use rsync. The thing I like about it is that it only backs up the changes to your files from the last time it backed up. This means each subsequent backup takes a small amount of time since it's not backing up every file. rsync also has an exclude switch, or you can list all your excluded items in a file and just reference that file in your command. Pretty slick.```
rsync -av --exclude-from=/path_to/excludes /from /to
```
where the file excludes is the list of items you don't want to back up. This help keep the command less cluttered.
You can also set up the rsync command to transfer the backup to another computer via ssh.

---

### Post by bwtranch on 2008-02-22
> **qpieus said:**
> I use rsync. The thing I like about it is that it only backs up the changes to your files from the last time it backed up. This means each subsequent backup takes a small amount of time since it's not backing up every file. rsync also has an exclude switch, or you can list all your excluded items in a file and just reference that file in your command. Pretty slick.```
rsync -av --exclude-from=/path_to/excludes /from /to
```
where the file excludes is the list of items you don't want to back up. This help keep the command less cluttered.
You can also set up the rsync command to transfer the backup to another computer via ssh.

Very good. Thanks, I think that is what I will use.

---

### Post by mivo on 2008-02-24
I also use rsync to back up my /home directory to an external disk. The below command only backups stuff that has changed since the last backup:

```

rsync -r -t -v --progress --delete /home/username/ /media/disk/backup-calico/home/username/

```

It also deletes files that were deleted in the source location. A good Gnome frontend for rsync is Grsync.

---

### Post by K.Mandla on 2008-02-24
+1 for rsync, or grsync.

---

### Post by bwtranch on 2008-02-25
Thanks everyone.

---

