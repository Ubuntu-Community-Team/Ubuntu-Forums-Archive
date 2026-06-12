---
title: "Sharing permissions to /var/www ?"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by PixelPixie on 2006-06-27
Disclaimer:  I am new to linux and Ubuntu (as in... I started using it last week.)

I am trying to put files into /var/www.  I can sign in as root using sudo nautilus and navigate to the folder and move files into it, but I can't create a new file and save it into that directory.

I've seen on the forums that you can use ‘chown –R username. /var/www’ to *change* the user who has permissions.  Is there a way to **add** permissions for myself while keeping the root permissions?

---

### Post by ProjectGod on 2006-06-28
create a new group.

add yourself into that group.

**sudo chgrp <newgroup> -R /var/www**

**sudo chmod -R g=rwx /var/www**

---

