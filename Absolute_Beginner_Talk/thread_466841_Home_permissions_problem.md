---
title: "/Home permissions problem"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by KiwiPete on 2007-06-07
I have inadvertently changed some of the folder / file permissions for  /Home  and now cannot boot into Ubuntu.
I can get into Terminal and use Sudo Nautilus to get to the various folders, but don't know what the permissions should be.
Help please..

KiwiPete

---

### Post by Najand on 2007-06-07
Use this command in a terminal:
```

sudo chmod -R 755 /home/USERNAME

```
Change USERNAME with your user name.
and try to reboot again.

---

### Post by justleen on 2007-06-07
/home permission should be:
Owner: root
Group: root
read write execute for root
read write for users
the /home/USER permission:
Owner: USER
group: USEr
read write execute for USER


as root:
```

chmod a+rw /home
chmod u+x /home

chown USER:USER /home/USER
chmod a-rwx /home/USER
chmod u+rwx /home/USER


```

---

### Post by KiwiPete on 2007-06-07
Thanks to both the above poetings - problem solved!
:-)

---

