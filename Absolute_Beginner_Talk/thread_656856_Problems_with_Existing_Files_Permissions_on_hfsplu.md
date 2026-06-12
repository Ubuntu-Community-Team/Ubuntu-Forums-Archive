---
title: "Problems with Existing Files Permissions on hfsplus external drive"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by constructotower on 2008-01-03
I recently started using an external hard drive that was originally formatted on macos (hfsplus). It mounts fine, I can read the existing files and write new ones. The problem is that I cannot do anything with the existing files (can't delete or modify). I've tried changing the permissions and owner with chmod and chown but the settings do not change. I've looked at other postings but most other peoples' situation is all or nothing (can't read or write at all). My problem is only with the files that already were on the drive. Any help greatly appreciated!

---

### Post by dcstar on 2008-01-03
> **constructotower said:**
> I recently started using an external hard drive that was originally formatted on macos (hfsplus). It mounts fine, I can read the existing files and write new ones. The problem is that I cannot do anything with the existing files (can't delete or modify). I've tried changing the permissions and owner with chmod and chown but the settings do not change. I've looked at other postings but most other peoples' situation is all or nothing (can't read or write at all). My problem is only with the files that already were on the drive. Any help greatly appreciated!

If you copy a file to your own filesystem can you then delete or modify it?

If so, you may want to consider copying off all the files, reformatting and then copying them back.

---

### Post by constructotower on 2008-01-04
> **dcstar said:**
> If you copy a file to your own filesystem can you then delete or modify it?

If so, you may want to consider copying off all the files, reformatting and then copying them back.

Yes, if I copy a file to the drive I can then delete or modify it.

It's a 250GB drive and my internal drive is only 80GB so copying and reformatting is not an option. Plus I want to leave the drive in the Mac format so that I can go back and forth between my Linux box and iBook.

---

### Post by dcstar on 2008-01-05
> **constructotower said:**
> Yes, if I copy a file to the drive I can then delete or modify it.

It's a 250GB drive and my internal drive is only 80GB so copying and reformatting is not an option. Plus I want to leave the drive in the Mac format so that I can go back and forth between my Linux box and iBook.

You really need to post the output of:
```
ls -al
```
of some of the files on the external drive that you cannot modify, this should show how Linux sees the security of these files.

---

### Post by constructotower on 2008-01-06
It's fixed now! I must have needed to restart and/or power down the drive after using the chown command because when I went to go get the output that dcstar requested I noticed that the ownership and permissions were now changed and I have full access to all the files on the drive, both old and new one. I didn't realize that a restart was necessary after making those changes. They DEFINITELY didn't take effect until I shut the computer down and restarted. Thanks for the help/suggestions.

---

