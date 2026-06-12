---
title: "help customizing .profile or .bash_login"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by jba6511 on 2007-09-18
I am not sure which one I need to edit - .profile or .bash_profile. I want to display a welcome message when a user logs in or accesses a terminal that includes their user name. Can someone point me in the right direction on how to accomplish this?

---

### Post by cmnorton on 2007-09-18
If the message is for all users, edit /etc/profile. You could also make this part of the default profile. Here is a thread that discusses it.

[http://ubuntuforums.org/showthread.php?t=99565](http://ubuntuforums.org/showthread.php?t=99565)

You can also take a favorite .profile, .bash_profile, .bashrc and place into /etc/skel for use when a new account is created.

---

### Post by jba6511 on 2007-09-18
thanks for the information. are there any examples of how to do this (editing profile)? I am still new to linux and do not want to make any changes without first being sure of what I am doing.

---

### Post by Celegorm on 2007-09-18
Make a backup of the file before editing it, then it'll be easy to restore it if you mess something up.

---

### Post by jba6511 on 2007-09-18
good idea. will try and play around to see if I can not figure out how to do this.

---

### Post by jba6511 on 2007-09-19
I have made a backup and tried to edit my .profile unsuccessfully. Can someone point me in the direction or provide some examples for how to get this done? I believe I am in the right file as .bash_login and .bash_profile do not exist in my home directory.

---

### Post by jba6511 on 2007-09-21
found the answer, sort of. Since I wanted to display a welcome message in bash for each user, I was able to do this by adding echo "welcome message....." to the .bashrc file at the end. I had to do this for each user though as I could not find a way to do it automatically for any user that logs in or opens bash. Any idea how to accomplish this?

---

### Post by kerry_s on 2007-09-21
in debian i use /etc/issue to display messages, it displays with out even having to log in.

```

Debian GNU/Linux lenny/sid \n \l
+-------------------------------+
|  Welcome! You may now log in  |
+-------------------------------+


```

---

