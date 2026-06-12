---
title: "Evolution: Cannot delete folder"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by g0m3z78 on 2007-02-10
Hi,

I'm using Evolution 2.8.1 and when I'm trying to delete a folder (called Read) I'm getting the following strange error message: 

Cannot delete folder "Inbox/Read".
Because "Could not delete folder `Inbox/Read':
Directory not empty".

The folder is empty and there isn't any sub-folder in it. Anyone has any idea how to solve this issue?

Thanks in advance,
g0m3z78

---

### Post by Spin Doctor on 2007-02-10
Strange...

Is it a folder which was created by Evolution, or a folder you created yourself?

Try renamning it, and deleting it if possible.

---

### Post by g0m3z78 on 2007-02-10
Thanks for your quick reply Spin Doctor. I created the folder and renamed several times already but it was not helped.

Regards,
g0m3z78

---

### Post by Spin Doctor on 2007-02-10
Ok. Try this then.

Go to your **homefolder**. Enable the view of hidden files **(CTRL+H)**

Go to **.evolution > mail > local > inbox.sbd**

Delete all files with the name of the folder you are trying to delete. 

Restart Evolution, and the folder should be history.

Hope this helps!!!

---

### Post by g0m3z78 on 2007-02-10
You are right! Under .evolution > mail > local > inbox.sbd I found a subdirectory for that Evolution folder and also checked the content of the mentioned subdirectory. There was one file there, which I removed. I deleted all files also from .evolution > mail > local > inbox.sbd with the name of the folder I looked for just to be on the safe side and now it's working fine.


Thanks for your quick support. That's why I chosen Ubuntu ;)
g0m3z78

---

### Post by Spin Doctor on 2007-02-11
Great it worked for you! Have a great day in Hungary!

---

