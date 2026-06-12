---
title: "Grsync"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by bern1939 on 2007-12-19
I have been using the excellent Grsync to backup.

The first backup takes some time obviously but thereafter just a few seconds was needed
to update any changes made to files.
But now when I try to  update files, the package goes through the entire process again as if it were doing the backup for the first time??

(Note: Only change I made was to set up a separate /home partition which I forgot to do on installation... would not have thought that that would have any bearing on the issue!)

Any ideas on this or is it considered normal?

Bern

---

### Post by kpkeerthi on 2007-12-19
When you moved the files to your new /home, the timestamps of the files changed. So rsync assumes that the files have changed and it is trying to sync all the files.

---

### Post by bern1939 on 2007-12-19
Thank you

Bern

---

