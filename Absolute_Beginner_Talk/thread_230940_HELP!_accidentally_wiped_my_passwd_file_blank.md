---
title: "HELP! accidentally wiped my passwd file blank"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by Soap_Dude on 2006-08-06
Are there versions automatically backed up by the system because I really don't want to reinstall? I know /etc/passwd~ would be my best bet. I've got a live CD, so I can do some file operations with it. However, I'm concerned about the permissions since I've got a blank passwd file. 

thanks

---

### Post by lamego on 2006-08-06
There are no backups from /etc/passwd unless you have edited it manually with an editor with takes care of backing up the file first.
If you do have a backup copy from the editor you should just need to copy backup file over the emtpy one.

---

### Post by Soap_Dude on 2006-08-06
Nope, never touched my passwd file before I noticed that I couldn't  **su** to other users. What about recovering the system defaults without reinstalling. Is there a pre-defined passwd file on install CD somewhere?

---

