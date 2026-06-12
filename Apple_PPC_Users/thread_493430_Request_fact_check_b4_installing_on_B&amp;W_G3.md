---
title: "Request fact check b4 installing on B&amp;W G3"
date: 2007-07-05
forum: Apple PPC Users
---

### Post by scav2000 on 2007-07-05
I'm planning on trying to install 7.04 on my B&W G3.

I have a drive with several partitions (ie, Mac style ones) on it.  One is a 4 gig one that's empty and I'm planning on using it for the install.

Now, if I understand everything I've read, in the install process I delete the partition on the 4 gig, turning it into Free Space.  

Then, I can use the choose the "Use largest continuous free space" option, and it'll correctly format and partition the 4 gig into a Root partion and a swap partition, all without touching the other mac-formatted partitions?

---

### Post by pxwpxw on 2007-07-05
> **scav2000 said:**
> I'm planning on trying to install 7.04 on my B&W G3.

I have a drive with several partitions (ie, Mac style ones) on it.  One is a 4 gig one that's empty and I'm planning on using it for the install.

Now, if I understand everything I've read, in the install process I delete the partition on the 4 gig, turning it into Free Space.  

Then, I can use the choose the "Use largest continuous free space" option, and it'll correctly format and partition the 4 gig into a Root partion and a swap partition, all without touching the other mac-formatted partitions?

That's what is meant to happen, but backups are always a good precaution.

However, 4GB might be a bit tight if you want a full ubuntu or kubuntu desktop and multimedia etc. It would depend on what other partitions you have/want.
If you have MacosX installed you can get a listing of all the existing partitions by using
 terminal.app and the pdisk command line utility.
```

 sudo pdisk -l

```

You  may be able to  use a Desktop install cd, or an Alternate install CD, but the Desktop CD may not be suitable if your mac is low on RAM.
I have not done an install on a B&W G3, so can't speak from experience, but will be interested in the result.

---

### Post by stmiller on 2007-07-06
In the OS X disk utility you should be able to delete the partition and leave it as unformatted free space. Then point the ubuntu installer to that partition. It will automatically create proper swap partition, and root directories in that space. 4GB will be tight...

---

