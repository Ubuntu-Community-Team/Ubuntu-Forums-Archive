---
title: "Gnome Search Tool"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by Buck2348 on 2006-12-21
I've been using Ubuntu for a couple of months now, and still can't quite figure out how the gnome search tool works.  I usually want to search the whole Ubuntu file system.  Starting from there it appears to me that the search never includes the /home directory.  If I have the search "include other file systems" it goes too far, including the mounted network shares.  Is there any way to have the search include /home in the file system?

Thanks,
Buck

---

### Post by bruenig on 2006-12-22
> **Buck2348 said:**
> I've been using Ubuntu for a couple of months now, and still can't quite figure out how the gnome search tool works.  I usually want to search the whole Ubuntu file system.  Starting from there it appears to me that the search never includes the /home directory.  If I have the search "include other file systems" it goes too far, including the mounted network shares.  Is there any way to have the search include /home in the file system?

Thanks,
Buck

Not sure if this will necessarily answer your question, I am a bit of a command line junkie. But, there are various search functions from the command line. You can do "whereis whatever" to search within the PATH. Or you can do "locate whatever" for a more expansive search. You can also do "find / -iname whatever" to search for directories with whatever. Hopefully this helped. "locate whatever" generally gives me the most responses, I would go with that.

---

### Post by Buck2348 on 2006-12-22
Thank you very much.

Buck

---

### Post by seijuro on 2006-12-22
also you may want to update the database locate searches every now and then particularly if you just installed a bunch of stuff. use: sudo updatedb

---

### Post by Buck2348 on 2006-12-23
Thank you.

---

