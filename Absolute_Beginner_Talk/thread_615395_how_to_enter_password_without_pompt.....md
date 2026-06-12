---
title: "how to enter password without pompt...."
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by mokkai on 2007-11-17
i want to create a script, which should automatically mount other one computer folder 
in my system through sshfs when i am login(it will prompt for password)...

how can i fix the password in my script (so it will not promt ,directly it will mount) ?

---

### Post by zhaozhou on 2007-11-17
You could write a line in /etc/fstab, then it'll mount as soon as your network is online.

---

### Post by mokkai on 2007-11-17
is there any idea to use ssh without prompt for password ?
like CPAU in windows(replacement of runas utility  which is @ [http://www.joeware.net/](http://www.joeware.net/))
then, how ?

---

