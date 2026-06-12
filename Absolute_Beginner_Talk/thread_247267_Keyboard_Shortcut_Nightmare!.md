---
title: "Keyboard Shortcut Nightmare!"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by spiral777 on 2006-08-30
OK, I tried running these two commands to make it so when I typed <Control><alt>Delete the system monitor would come up. Unfortunately that doesn't work. What happens is everytime I hit Delete by itself the monitor comes up, making it almost impossible to change text. Grrrr. How can I reverse this and get it to do what I want it to?

```

gconftool-2 --set --type string /apps/compiz/general/allscreens/options/command1 "gnome-system-monitor"


gconftool-2 --set --type string /apps/compiz/general/allscreens/options/run_command1_key "<Control><Alt>Delete"
```

---

### Post by spiral777 on 2006-08-30
Anyone know what I can do? Even if I was just to get it so delete key didn't pull up the system monitor it would be fine.

---

### Post by PPAAUULL on 2006-08-30
I will tell you what to do. Go out and download Automatix. It will set up ctrl alt del to do exacly what you want and the best thing is you don't even have to really do anything 'cause automatix does it for you.

---

### Post by spiral777 on 2006-08-30
I'd really rather not. I don't like Automatix because it seems to work in non-productive ways. I'd rather just get this straightened out.

---

