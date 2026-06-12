---
title: "File system wrong size ?"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by simons-photography on 2008-02-16
I installed Ubuntu hey nothing went wrong not incompatibility problems, then, after booting into windows and back to ubuntu I startup and it tells me the file system size of dev/sd3c (my linuc partition I think) should be "x" size but instaed was something else, so I press ctrl alt del thinking I'll reboot and it continues booting ubuntu, now the first time it worked the second time I put in my user and pass it started to load and then went back to user and pass and so on round in circles. now that is all it will do. what can I do ? just reinstall (like windows I hope not this is supposed to be stable not more f ucked up than windows)

---

### Post by taurus on 2008-02-16
At the GUI login screen, press <Ctrl><Alt>F2 and log in with your name and password.  Then, post the outputs of these commands from a prompt.

```
df -h
sudo fdisk -l
cat /etc/fstab
```

---

### Post by simons-photography on 2008-02-16
ok I'll give it a go later thanks

---

### Post by asmoore82 on 2008-02-16
> **simons-photography said:**
> I installed Ubuntu hey nothing went wrong not incompatibility problems, then, **[COLOR="Red"][SIZE="2"]after booting into windows and back to ubuntu[/SIZE][/COLOR]** I startup and it tells me the file system size of dev/sd3c (my linuc partition I think) should be "x" size but instaed was something else, so I press ctrl alt del thinking I'll reboot and it continues booting ubuntu, now the first time it worked the second time I put in my user and pass it started to load and then went back to user and pass and so on round in circles. now that is all it will do. what can I do ? just reinstall (**[COLOR="Red"][SIZE="2"]like windows I hope not this is supposed to be stable not more f ucked up than windows[/SIZE][/COLOR]**)[emphasis added]

#-o add this to that list of stuff to run from the console:```
date
```

---

### Post by simons-photography on 2008-02-16
hehe yes i see you got my meaning

pk so I put date after the other commands ?

---

### Post by simons-photography on 2008-02-16
you will find attached screenshots of the responses naturally they are double dutch to me mostly

---

