---
title: "more access problems"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by davidexe on 2007-11-26
And the problems keep coming.  I was able to reset the access on all the folders on the server, at least for those that map to it. However, now if one user creates a file it becomes read only when loaded on someone elses computer.

Can anyone tell me what needs to be changed so one user mapped onto the server can create a file and save it and then another user can open it and modify it (R/W access)?

Thanks.

---

### Post by davidexe on 2007-11-26
Problem solved. It appears that I hadn't really done what I thought I had done before.  This time I tried a different format on the command and it worked.  I had not set the access rights correctly.  used a -a instead of an a=rwx.

So, thanks for all the preious help that allowed me to figure this one out.

---

