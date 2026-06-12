---
title: "[SOLVED] how to copy etc"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by DarinB on 2007-09-23
silly beginner question i want to copy my etc folder to an external hard drive as a backup how do i do it??
when i drag it over it gives the message not all files will be copied you do not have access???

---

### Post by RomeReactor on 2007-09-23
Hi. If I had an external HD mounted in **/media/hdx**, then I would do:
```
sudo cp -r /etc /media/hdx
```

Or you could open Nautilus as root (using gksudo):
```
gksudo nautilus
```
and then copy the folder as you previously intended. Just remember to be very careful while Nautilus is open this way, and close it as soon as you finish copying the folder.

---

### Post by floke on 2007-09-23
Since /etc is not within your /home dir. you need root permissions.
Fire up nautilus with 'gksu nautilus' from the terminal, and drag and drop then.
Close nautilus when done - you don't want to be running as root longer than need be.

---

### Post by schallstrom on 2007-09-23
Sounds to me that you are trying to copy /etc as a normal user. In Ubuntu Linux (as in every other Unix-like OS) some files in /etc are not readable for normal users due to security reasons. So you would have to copy /etc with root user privileges. The easiest way to do that is with the CLI. Do something like this:
```

$ sudo cp -a /etc /media/your-external-harddrive

```

The -a is for "archive mode" which preserves file ownership and permissions, which is a good idea when making a backup of /etc.

---

### Post by DarinB on 2007-09-23
i tried 
gksudo nautillus i got 
darin@darin-desktop:~$ gksudo nautillus

(gksudo:6299): Gtk-WARNING **: Theme directory 48x48/mimetypes of theme Snow-Apple has no size field

????

---

### Post by DarinB on 2007-09-23
i now tried 
sudo cp -a /etc /media/disk as above
it copied all of the folder 
but it now has a lock on it what does that mean will i be able to copy it back if i need to??

---

