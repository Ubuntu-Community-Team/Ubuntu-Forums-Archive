---
title: "CD-rom name change, can't mount now"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by ./Coffee on 2007-03-02
My issue is I booted my computer up about a week ago and it said there were no cd-roms, so I checked my BIOS and everything was there but I noticed that the names of the drives had changed so I was wondering if there is a way to re-detect them?


I have been using ubuntu for a about two years and usually can resolve these things; However I can't figure this out for the life of me.

---

### Post by terdon on 2007-03-17
Could you post your /etc/fstab file please? Also the output of this command: ```

sudo cdrecord --scanbus

```

---

### Post by ./Coffee on 2007-03-18
The problem was fixed so sorry I thought I had posted that it was fixed. The problem was my CD-rom cord went bad and the mother board gave them some weird name trying to guess what and where they were.

---

