---
title: "How would you sync between a windows pc and ubuntu?"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by blop on 2007-05-20
HI all, i need some advice as to how to sync files between 2 pcs over a home network. 

I want to sync My Documents on my XP machine with a folder on my Ubuntu laptop...


what programs are there that will do that? I need to it to do an auto scan and move only the recently modified files....so i have a perfect mirror copy as much as possible.

cheers

---

### Post by rich.bradshaw on 2007-05-20
rsync is what you want.

You can run it in cygwin in Windows. I think lifehacker did an article about how to do it.

---

### Post by blop on 2007-05-20
rsync.... ok ill check it out..


cheers

are you any good with sound issues...i have a post that im getting no help on....


many thanks

---

### Post by kh4nh on 2007-05-20
Here is the guide on installing and configuring **_[rsync and ssh]("http://optics.ph.unimelb.edu.au/help/rsync/rsync_pc1.html")_** on windows (without full Cygwin)

Good luck

---

### Post by blop on 2007-05-20
thanks for that link, but i want to do it slightly differently i wish to run rsync or whatever application from my linux laptop.....to sync my windows folder on to it.....

im having problems trying to work out to access the samba shares from command line

---

### Post by EddieT on 2007-06-12
Here is a good guide that helped me out:
[http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)
Once the share is mounted than you should be able to sync with no trouble using Grsync

---

