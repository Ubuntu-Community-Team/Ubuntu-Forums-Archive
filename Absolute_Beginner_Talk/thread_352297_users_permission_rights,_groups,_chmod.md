---
title: "users permission rights, groups, chmod"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by iulian on 2007-02-03
Hello, I have Ubuntu 6.10 server. I try to copy a file into /var/www/ i have no rights to do this. How can I copy some files into that directory?

---

### Post by xmastree on 2007-02-03
The easy way is to run the comand as root:

**sudo cp /path/to/the/file/filename /var/www**

---

### Post by iulian on 2007-02-03
Yes, but I was on a windows machine using WinSCP to copy files to server. I changed owner of the www to myself. I have another question now... How can I see all groups and users on my machine? And, a little big offtopic: if I install cvs on linux server I will be able to commit files from a window machine?

---

