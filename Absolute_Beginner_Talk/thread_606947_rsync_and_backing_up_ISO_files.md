---
title: "rsync and backing up ISO files"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by mmathur on 2007-11-08
I am using rsync to backup .ISO files to a NAS device on a daily basis.  The problem is that rsync is copying ISO files to the NAS which have already been copied and the ISO files have not changed in the source area.

Here is the command that I am using for rsync:
rsync -r /media/mythtv/ /media/NDrive/MediaServer/

Can anyone explain why rsync is copying over the ISO files which already exist in the destination folder and the files are identical to the source?  Also, please let me know if I am leaving out a specific flag that will allow rsync to skip files that already exist (which I thought was a feature of rsync).  Thank you.

---

### Post by lakris61 on 2007-11-08
You should use the -a switch, for archive mode.
I think. That's what i always use for backup purposes.

---

### Post by RTrev on 2007-11-08
Just learning rsync, but found that the initial backup took an hour or so, including many iso files.  Subsequent trys took less than a second.  I'm using:

```
rsync -av /home/bob/Data1 /media/disk
```

If I run it as my normal user account, I get a bunch of errors about not being able to change some group permissions, but the backup seems fine.  If I run it with sudo, I get no errors and again the backup seems fine.

Not sure what I'm doing yet, but it seems that the -r to recursively go into sub-directories is not needed.  Why it's there I have no idea.  HTH.

bob

---

### Post by hyper_ch on 2007-11-09
what file system do you have on the NAS?

---

### Post by lakris61 on 2007-11-10
> **RTrev said:**
> Just learning rsync, but found that the initial backup took an hour or so, including many iso files.  Subsequent trys took less than a second.  I'm using:

```
rsync -av /home/bob/Data1 /media/disk
```

If I run it as my normal user account, I get a bunch of errors about not being able to change some group permissions, but the backup seems fine.  If I run it with sudo, I get no errors and again the backup seems fine.

Not sure what I'm doing yet, but it seems that the -r to recursively go into sub-directories is not needed.  Why it's there I have no idea.  HTH.

bob

It could be that the target file system doesn't support the same set of file flags as Your source, it could also be that You are not allowed to set for example permission or owner; ie a normal user can't set ownership of a file to another user. If the source is readable it will be saved with current user as owner.

The -a switch stands for archive mode, and it is comprised of several other flags, including recursive mode.

/Lakris

---

### Post by RTrev on 2007-11-10
> **lakris61 said:**
> It could be that the target file system doesn't support the same set of file flags as Your source, it could also be that You are not allowed to set for example permission or owner; ie a normal user can't set ownership of a file to another user. If the source is readable it will be saved with current user as owner.

The -a switch stands for archive mode, and it is comprised of several other flags, including recursive mode.

/Lakris

I think I see the problem.. that -a switch was doing a lot more than I actually cared to have it do!  I should have read the man pages more carefully!  :)

When I first got the external drive I put an ext3 filesystem on the entire thing, since we don't use Windows at all here.  One thing I do on my other disks that I don't on the external is mount them with the noatime,nodiratime options, as it's supposed to be a bit quicker on reads.  I can't do that on the external because I have no fstab entry for it at all.

When I looked at what -a was doing, it included trying to set group and owner privs, etc., which is where I was getting errors.  Running with just -rv is really what I think I want, and that works just fine without requiring sudo.

I was so used to ls -a that I just used -a without really looking it up, although I admit I was puzzled that it was recursing without being told to.  :rolleyes:

All I really want is a dup of what's on the RAID array, so it seems that -r will get all the directories and -v will just let me see what it's doing.  

Thanks much!

Bob

---

