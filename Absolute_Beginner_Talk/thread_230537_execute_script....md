---
title: "execute script..."
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by in_orbit on 2006-08-06
Hi, I have written an bash shell script which can be executed by typing './script arg' when I'm in the right directory. Is there some way of making the script acting like a global program, for example skype, which every user can reach? I want every user to be able to just write 'script arg' in order to execute the script. I hope that made any sense.

Regards
/In orbit

---

### Post by tartarian on 2006-08-06
Could you not just put it in / (root) and set the file permissions (chmod 777) so that all users can access it. Then you would just type /.script name into konsole/terminal

---

### Post by kabus on 2006-08-06
Put it in /usr/bin

---

### Post by steve.horsley on 2006-08-06
put it in /usr/local/bin.

Make sure the permissions say it's world readable and world executable.

---

