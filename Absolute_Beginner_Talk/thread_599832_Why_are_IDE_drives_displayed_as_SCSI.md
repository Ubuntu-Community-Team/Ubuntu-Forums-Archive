---
title: "Why are IDE drives displayed as SCSI?"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by eapache on 2007-11-01
I've been using Ubuntu since Dapper, and I'm just wondering why all IDE drives are still displayed as SCSI?

As far as I can remember, this originated in a bug in the kernel that made it into Edgy (and couldn't be replaced because of the code freeze). The devs decided not to update it during Edgy's cycle because it would possibly break peoples' fstab etc. but I just realized that it still happens in Gutsy...

Is there a reason for this?

---

### Post by cmnorton on 2007-11-01
I believe it started with a version of the kernel and has to do with how the drives are initialized.

---

