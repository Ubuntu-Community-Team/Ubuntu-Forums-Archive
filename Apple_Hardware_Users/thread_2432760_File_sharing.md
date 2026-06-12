---
title: "File sharing"
date: 2019-12-08
forum: Apple Hardware Users
---

### Post by ozfrog on 2019-12-08
Hello,
MBPro 10.14.6, Ubuntu installed on a 32 G USB drive - persistent, and works fine.
I would like to be able to access files on the MacOS internal SSD drive from the Ubuntu GUI
At a loss.
Thanks

---

### Post by TheFu on 2019-12-08
OSX uses HFS+. Need to install the helper packages to access that sort of foreign file system.
Then just need to mount it somewhere.

```
sudo apt-get install hfsprogs
sudo mount -t hfsplus -o force,rw /dev/sdXY /media/mntpoint
```

/media/mntpoint is just an empty directory that must already exist. Create one if it doesn't. You can do this almost anywhere, but for temporary mounts, either /media/ or /mnt/ are ok directories to place the empty directory into.

If there is an error mounting, try remounting.

When you are done, either reboot or **umount**.

After this is working, you can seek out more GUI-friendly methods.

---

### Post by gsahli on 2019-12-09
I think it's easier than that with samba (which both MacOS and ubuntu have by default):
[https://support.apple.com/guide/mac-help/share-mac-files-with-windows-users-mchlp1657/mac](https://support.apple.com/guide/mac-help/share-mac-files-with-windows-users-mchlp1657/mac)

---

### Post by TheFu on 2019-12-09
> **gsahli said:**
> I think it's easier than that with samba (which both MacOS and ubuntu have by default):
[https://support.apple.com/guide/mac-help/share-mac-files-with-windows-users-mchlp1657/mac](https://support.apple.com/guide/mac-help/share-mac-files-with-windows-users-mchlp1657/mac)

I could be wrong, but the OP isn't using networking. Correct? 

The disk is local just with an OSX file system, so it is either a dual boot or single-Ubuntu boot setup.  Samba uses networking .... i.e. 2 different systems concurrently running.  

But I could be wrong. Won't be the first time, today. ;)

---

### Post by gsahli on 2019-12-16
'Doh --
Sorry for mis-reading and confusing the issue.

---

