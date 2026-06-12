---
title: "[SOLVED] Two cdroms and Amarok"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by .nedberg on 2008-01-02
Hi

I just started prepping one of my spare computers for sale, and installed Kubuntu Gutsy. The computer has one DVD-ROM and one CD-RW burner. I just wanted to test both and inserted a CD in one of the and clicked "play audio cd with amarok". It played just fine! I then ejected the CD and inserted it in the other CDROM and again clicked "play audio...". Amarok says it "could not insert nothing into playlist".

Amarok is set to use /media/cdrom as cd device. I think the first time I insert the cd it will be mounted with /media/cdrom as an alias, but the alias is not released when I insert it the other time.

```
amarok --cdplay /dev/<other cdrom>
```

works fine.

Any idea? Should I just keep it this way or is there somthing I could do (short of removing one of them)?

---

### Post by blueridgedog on 2008-01-02
On my system /media/cdrom is just a symlink to /media/cdrom0

```
lrwxrwxrwx  1 root  root     6 2007-12-02 06:04 cdrom -> cdrom0
drwxr-xr-x  2 root  root  4096 2007-12-02 06:04 cdrom0
drwxr-xr-x  2 root  root  4096 2007-12-02 06:04 cdrom1
```

So, incerting a disk into the cdrom1 device will not work for programs that look for /media/cdrom.

Perhaps the symlink is designed to change when you insert media, but I don't observe that.

---

### Post by .nedberg on 2008-01-03
> **blueridgedog said:**
> 
Perhaps the symlink is designed to change when you insert media, but I don't observe that.

That is the problem! The way it is now I can not play CD's with both drives (not in a easy-gui-way). But /media/cdrom0 is not the same drive on every boot. It depends on what drive I use first.

Thank you for answering! I will sell the computer as it is!

---

