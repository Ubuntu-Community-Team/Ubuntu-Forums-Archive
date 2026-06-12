---
title: "Pathing Question"
date: 2006-01-13
forum: Absolute Beginner Talk
---

### Post by seekyrr on 2006-01-13
I have some apps that I can only launch from the folder they reside in.  Other apps i can launch from anywhere in terminal.

Is there a command I can run to link or make a path for apps?

Thanks

Seek

---

### Post by Mr_Grieves on 2006-01-13
You probably mean:

/usr/local/bin (regular user programs)
or
/usr/local/sbin (mostly admin programs)

Depending on what kind of "application" you program has.

---

### Post by super on 2006-01-13
application binaries/links are usually placed in /usr/bin or /usr/local/bin. placing them here will make them global. meaning they can be run from any directory without specifying a path.

just make a link to the binary and place the link in /usr/local/bin. you'll may need to change the permissions on the link and the binary if you have more than one user on to allow them to execute the file also.

EDITED after seeing mr_grieves' post.

---

