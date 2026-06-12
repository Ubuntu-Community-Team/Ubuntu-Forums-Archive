---
title: "problem with gFTP"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by DBGOTD on 2006-12-20
Hey, new gnu/linux user here, complete convert after doing a research project on it for my hardware and software systems class. But as anyone, still having problems.

In XP I used Filezilla and never had a problem. I downloaded gFTP to be able to manage my FTP, but when I uploaded some stuff this is the response I got when I tried to load the page:

Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Fatal error: Unknown: Failed opening required '/home/jpcamara/public_html/practice/form.php' (include_path='.:/usr/lib/php:/usr/local/lib/php') in Unknown on line 0

It almost seems like it's trying to access it from my computer? I'm not really sure and I've never experienced a problem like this when using Filezilla or smartFTP...so any help?

---

### Post by chippy99 on 2006-12-20
This looks more like a problem with your php than a problem with gftp. 
Are you trying to include a file with the local path name (Failed opening required '/home/jpcamara/public_html/practice/form.php) instead of using the corect path on the server ?
What happens if you download the file you uploaded, is it the same as the original file ?

---

