---
title: "backup gone wrong"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by guitarmaniac on 2007-02-24
OK heres what happened.
I just bought a new hard drive because my old one was failing, so I tried to back up my system using this guide [http://doc.gwos.org/index.php/Backup_restore_system](http://doc.gwos.org/index.php/Backup_restore_system) but for some reason, after three hours it still had not finished so I stopped it and deleted the tar file. I was going to try again after rebooting, but for some reason, now my hard drive is so full, I can't log in unless I use a failsafe gnome session.
I uninstalled openoffice clipart (ticking completely remove in synaptic) to free up some space, but it still wouldnt log in normally!
what could possibly be the problem?

---

### Post by louis_nichols on 2007-02-24
That backup archive, did you delete it or just send it to Trash? If you sent it to trash, you have to empty that. Now, if you can't login in the graphical manager, it's still done easily. When the login scren comes up, don't try to login yet. Press CTRL+ALT+F1 to get a terminal prompt and login there. then issue this command: ```
$ cd ~/.Trash
$ sudo rm -r *
```
After this, press CTRL+ALT+F7 and try logging in again.

---

### Post by guitarmaniac on 2007-02-24
my home partition is seperate to my root partition and my Trash folder is empty.
:confused: :confused: :confused:

---

### Post by louis_nichols on 2007-02-24
Can you post here the output of the commands ```
df -h
``` and ```

mount
```

please?

---

### Post by guitarmaniac on 2007-02-24
ok, turns up the tar file was in /root/.local/share/Trash/ (must have been running the file manager as root or something?).
Thanks anyway though, wouldnt have thought to look in the trash, as usually I press shift delete to delete things, which bypasses the trash can. Must have been too lazy to press the shift button this time :P

---

### Post by louis_nichols on 2007-02-24
OK. glad it's sorted.

---

