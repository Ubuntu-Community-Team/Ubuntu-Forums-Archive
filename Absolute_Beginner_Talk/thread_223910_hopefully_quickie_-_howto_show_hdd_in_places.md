---
title: "hopefully quickie - howto show hdd in places?"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by justicerulesok on 2006-07-27
I have a second hdd which is mounted it is in fstab and gparted and the device manager.

is there some kind of 'show' command I can use to get it to be seen in 'places' 'computer'

Thanks.

Justice.

---

### Post by OpsVentus on 2006-07-27
You have to give it the "user" option in your fstab for hdd. This way Ubuntu thinks it's media and will put it in 'places'.

Cheers,
Bart.

---

### Post by justicerulesok on 2006-07-27
do i need to remove the word defalts or add user as well as defalts?  if the latter do i need to comma seperate?

Thank you for helping me out :-) (& thanks for a simple answer)

---

### Post by moma on 2006-07-27
This command 
$ sudo /etc/init.d/dbus restart 
will refresh the Places menu and Desktop after I've commented out a line (harddrive) in /etc/fstab. The drive disappers from the menu and desktop. But the opposite does not work. 

Try to refresh desktop by pressing: CNTR + ALT + BACKSPACE.

---

### Post by OpsVentus on 2006-07-27
You have to replace the default for 'user,rw'.
This way it will apear in places and will still be writable by users.

Cheers,
Bart.

---

