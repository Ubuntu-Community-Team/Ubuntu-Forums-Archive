---
title: "Backup RAID-1 to external USB"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by RTrev on 2007-11-06
Basic scenario

My system disk is a little 74G Raptor.

I have two 500G internal SATA drives which are using mdadm in RAID-1.

I have an external 500G USB drive that I want to use for backups.

I'm running Gutsy 64-bit, and it's the only OS on the system.

How can I best copy all of the data from the RAID-1 array to the external USB drive?

Sorry if I've left out anything critical.. I'm trying to be succinct.  :)

Thanks,
Bob

---

### Post by kidders on 2007-11-08
Hi there,

The _best_ approach is a personal choice, really. In theory, you have two choices, I suppose...

**Disk imaging**
You could dump a byte-for-byte copy of one of your RAIDed disks onto the external one. Then, if you needed to restore the backup at some point in the future, you could swap the external disk for an internal one, and reconstruct your array based on the old image ... essentially "roll back" your array to a previous state.

**A standard copy**
You could simply copy files from your array to the external disk, giving yourself the option of restoring one or two files, without having to revert the entire array. You could also use tools like rsync to avoid duplicating unaltered data between backups.

Either approach would allow you to use compression to (possibly) fit more than one backup onto the same external disk.

Whichever approach you choose, you need to take care to produce a consistent backup. In other words, it's best not to try to modify any of your files while the backup is in progress. I would suggest an automated approach ... perhaps a scheduled backup at 3am every second day, or something, that checked nobody was logged in, before proceeding. A simple cron job like **[ -z "`users`" ] && echo cp -a /mnt/raid /mnt/backup** would be a good starting point, at least.

---

### Post by RTrev on 2007-11-08
> **kidders said:**
> Hi there,

The _best_ approach is a personal choice, really. In theory, you have two choices, I suppose...

**Disk imaging**
You could dump a byte-for-byte copy of one of your RAIDed disks onto the external one. Then, if you needed to restore the backup at some point in the future, you could swap the external disk for an internal one, and reconstruct your array based on the old image ... essentially "roll back" your array to a previous state.

**A standard copy**
You could simply copy files from your array to the external disk, giving yourself the option of restoring one or two files, without having to revert the entire array. You could also use tools like rsync to avoid duplicating unaltered data between backups.

Either approach would allow you to use compression to (possibly) fit more than one backup onto the same external disk.

Whichever approach you choose, you need to take care to produce a consistent backup. In other words, it's best not to try to modify any of your files while the backup is in progress. I would suggest an automated approach ... perhaps a scheduled backup at 3am every second day, or something, that checked nobody was logged in, before proceeding. A simple cron job like **[ -z "`users`" ] && echo cp -a /mnt/raid /mnt/backup** would be a good starting point, at least.

Thanks for the ideas!  I've been looking at dd and rsync but thought they might be too big a hammer for this job.  :)

As I was reading this I had a crazy (?) thought: what if I were to just periodically add the external drive to the RAID array, wait until the RAID is clean, and then remove it again?  This is just for data storage.  Any advantages or disadvantages over the other ideas?

Thanks again!

Bob

---

### Post by psusi on 2007-11-08
You could also use tar for backup.  It will compress the backup file and can be configured for incremental backups.  You can also choose to restore the whole thing or just extract specific files.  

I would suggest going with rsync though, since you won't really need compression since the external disk is just as large as the internal one.  The other advantage rsync has is that after the initial backup, subsequent updates will be MUCH faster, and unlike with tar, incremental rsync backups can be done forever without the need for another full backup, or increasing risk of data loss.

---

### Post by kidders on 2007-11-08
> **RTrev said:**
> Thanks for the ideas!  I've been looking at dd and rsync but thought they might be too big a hammer for this job.Hehe not really ... they're pretty basic little utilities, useful for lots of things. Don't forget about plain old "cp" either. :-)

Your "crazy" idea isn't that wild, when you think about it. Off the top of my head, the disadvantages are:[LIST]
[*]If you needed one file back, you would probably have to restore the entire backup image.
[*]You'd need a basic working knowledge of mdadm to make use the backup.[/LIST]If you actually wanted to try it, it's vital to (a) flush your I/O buffers, and (b) drop the external disk from your array in software first, before unplugging it. That way, you can be *sure* nothing odd will happen. So, your command sequence would look something like...```
sync
mdadm --fail ...
mdadm --remove ...
(Unplug device)
```One other thing: If you make a backup this way, and want to update it at some point, you may find that mdadm will recognise your external drive as having a RAID array on it, and might be reluctant to let you overwrite it. To save yourself any confusion, and the hassle of having to "--force" commands (which can make some people nervous they're doing the wrong thing), you could use "dd" to destroy the RAID metadata towards the beginning of your external device. So, if you wanted to, you could try writing yourself a little script, something along the lines of...```
# Some sort of test, to check we're not about to do something stupid!
if [ "`udevinfo -a -n /dev/sda|grep model|cut -d= -f3`" != "model name" ]; then
     echo "The connected USB device is the wrong disk!"
     exit 1
end

# Deliberately screw up the start of the disk's data
dd if=/dev/zero of=/dev/sda count=100M

# Add the external device to the array for a while
mdadm --add ...

# Sit about while the array reconstructs itself
while [ -n "`grep recovery`" ]; do
     sleep 30
done

# Eject the external disk
sync && mdadm --fail ...
mdadm --remove ...
```This probably won't be *quite* right as it stands, but something along these lines should do the trick for you. Having said all that though, my personally preferred backup method is simply to copy a tarball of my important data to another computer ... pretty low tech!

**Edit:** Yay! Psusi agrees. :-)

---

### Post by RTrev on 2007-11-08
> **psusi said:**
> You could also use tar for backup.  It will compress the backup file and can be configured for incremental backups.  You can also choose to restore the whole thing or just extract specific files.  

I would suggest going with rsync though, since you won't really need compression since the external disk is just as large as the internal one.  The other advantage rsync has is that after the initial backup, subsequent updates will be MUCH faster, and unlike with tar, incremental rsync backups can be done forever without the need for another full backup, or increasing risk of data loss.

Let me do some study of rsync.. it sounds like a good solution.  I've never really looked into what it can do, but it's sounding good.  Thanks.

---

### Post by RTrev on 2007-11-08
> **kidders said:**
> snip

 Having said all that though, my personally preferred backup method is simply to copy a tarball of my important data to another computer ... pretty low tech!

Yeah, I'm beginning to see that simply doing it that way has a lot of advantages, or at least doesn't suffer from the disadvantages some of the others do.  :)

Thanks.. think I'll make some tarballs and see how the best way to do that would be.  I have Gigabytes worth of things which don't really require backup, and currently only a small batch of things I'd hate to loose.. source code, HTML, personal documents, and so on.

Thanks!

---

### Post by psusi on 2007-11-08
rsync is basically a super cp that tries to reconigze if some of the files, or even only chunks of those files, are already on the destination, so it can avoid having to copy them again.  That way even if you have a number of large files that you make small changes to every day, you can do a nightly backup very quickly because only the changed parts need copied.  

One handy feature about it is that the backed up files are just normal files which you can access like you would any other file, rather than having to say, untar them.

---

### Post by RTrev on 2007-11-08
> **psusi said:**
> rsync is basically a super cp that tries to reconigze if some of the files, or even only chunks of those files, are already on the destination, so it can avoid having to copy them again.  That way even if you have a number of large files that you make small changes to every day, you can do a nightly backup very quickly because only the changed parts need copied.  

One handy feature about it is that the backed up files are just normal files which you can access like you would any other file, rather than having to say, untar them.

So were talking about "incremental" backups, basically?  That would be a good solution too.

Since my backup drive is the same size as my RAID-1 array, it should all fit.

One related issue that complicates all of this is that I don't know how the external USB should be mounted.  It's not in fstab, and permissions apparently depend on what user has plugged the drive in.  So if I leave the drive connected and reboot, it becomes owned by root.  If I log in and then connect the drive, it's owned by me.  That probably doesn't matter for this job.. as I can always access the drive via sudo if I need to.  Since my 500G RAID-1 is only using a fraction of the available space (I've read that this is best for Linux in terms of fragmentation.. keep a lot of free room on the drives..)

Thanks again.. will do some experimenting!  :)

---

### Post by psusi on 2007-11-09
Yes, you will need to run rsync with sudo anyhow so it can maintain the file ownership and permissions when it copies them.

---

### Post by RTrev on 2007-11-09
> **psusi said:**
> Yes, you will need to run rsync with sudo anyhow so it can maintain the file ownership and permissions when it copies them.

Okay.. thanks.  It's looking good!

---

### Post by digitalbenji on 2007-11-09
I think that the tarball solution is the best if you want to copy just a few files and you are interested in compression.  If you don't care about compression, use rsync, and you'll have a mirror of the files you want.  I would be reluctant to add a USB drive to a software RAID array, because it could adversly affect performance (USB is slowww), and because even in the best case recovery scenario, you likely would not want to put the USB disk online as part of the RAID to be used normally.  If you want to copy everything (including the master boot record) then use dd.  If you only care about the data files, I'd go with either rsync or tar.

---

### Post by RTrev on 2007-11-09
> **digitalbenji said:**
> I think that the tarball solution is the best if you want to copy just a few files and you are interested in compression.  If you don't care about compression, use rsync, and you'll have a mirror of the files you want.  I would be reluctant to add a USB drive to a software RAID array, because it could adversly affect performance (USB is slowww), and because even in the best case recovery scenario, you likely would not want to put the USB disk online as part of the RAID to be used normally.  If you want to copy everything (including the master boot record) then use dd.  If you only care about the data files, I'd go with either rsync or tar.

Thanks..  so far the rsync solution seems perfect for my needs.  The RAID solution I hadn't really thought out very well, and I agree it doesn't sound like a wise choice.

---

