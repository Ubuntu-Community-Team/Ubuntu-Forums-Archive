---
title: "Need help with fstab settings"
date: 2012-08-28
forum: Any Other OS
---

### Post by bobsmith2 on 2012-08-28
I am having a problem with Truecrypt and I'm wondering if my fstab file needs to be edited in order for Truecrypt to work correctly. The problem is this: Whenever I try to copy a large file (~100 MB or more), Truecrypt seems to start the process and then just stop after about 89 MB. My Truecrypt container is located on my ntfs drive so that I can access it with XP. I can run any file from Truecrypt with no problem, and I can copy large files OUT of the Truecrypt container with no problem... it is only when I try to _*write*_ to the Truecrypt container with a file over 100MB or larger that the process either stops, or slows to a crawl after a few seconds.

Here is the fstab line in question:

```
UUID=0GBC2E4RDGHIUF00 /mnt/Disk2Bkp ntfs-3g auto,user,rw 0 0
```

Here is the output from the mount command:

```
/dev/sdb5 on /mnt/Disk2Bkp type fuseblk (rw,noexec,nosuid,nodev,allow_other,blksize=4096)
```

I'm wondering if Truecrypt needs some setting I left out.

So far I have uninstalled Truecrypt and reinstalled. I even tried the older version. I also created a new Truecrypt container with both the new version and the older version, thinking that maybe the container was corrupted, but the problem persists. I also tried removing "user" from the fstab line. I should add that I duel-boot and Truecrypt in XP writes perfectly to the same container.

I'm hoping someone here can help me modify fstab so Truecrypt will work. Or if someone who has Trucrypt writing to an ntfs drive with no issues would post their fstab file contents, that would help as well.

I'm actually using Mint 13 (12.04 derivative), but nobody in the Mint forum seems to be able to help. I have tried Truecrypt's forum, but that is a ghost-town. I'm hoping someome here will be able to shed light on the issue. Thank you.

---

### Post by Perfect Storm on 2012-08-28
Moved to Other OS/Distro Talk.

---

