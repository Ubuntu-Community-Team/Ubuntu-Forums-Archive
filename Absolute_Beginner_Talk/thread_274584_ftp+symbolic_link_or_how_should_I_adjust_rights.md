---
title: "ftp+symbolic link or how should I adjust rights"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by mee.six on 2006-10-10
Hello people :)

   I have a problem here: I installed ftp server (vsftpd, the first one I've found in synaptic :)) and want to add a symbolic link to one of my dirs into it's root.
  But looks like "ftp" user doesn't have permissions to list and read files.. a switched directory's group to "users", set "+r" to anybody, but... it still doesn't work. 

Any suggestions on this topic?

---

### Post by mssever on 2006-10-10
Directories require execute permissions (+x) as well as read permissions.  Do chmod +rx dirname on the directory (and all parents, if necessary). Strictly speaking, both read and execute permissions aren't necessary in every situation, but I don't recall the distinction at the moment. One allows the reading of files in the directory, and the other allows the listing of files.


Switching the directory's group won't do anything unless you change it to a group that the FTP server is a member of (which probably isn't users).

---

