---
title: "screwed myself with usermod"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by jakihairi on 2007-06-28
I just screwed myself with usermod, I was trying to add myself to a new group. I was the administrator, but now I am not:(. I read the man page before executing this command, I just wasn't thinking straight i guess:(
```

sudo usermod -G anewgroup myusername

```
I don't think there's a way to login as root since ubuntu doesn't allow this  (without first enabling this option, which requires root access), and since i'm not a member of the administrator group anymore(and no one else is an administrator), I can't do much of anything on my computer! Is there a way to fix this with a rescue cd? Please help me avoid a reinstall!

thanks,
Rob Callan

---

### Post by chandler on 2007-06-28
You'll have to load up the livecd, then mount the partition.  Then you're going to look for the file /etc/passwd and do some changes.  this is the format of the file:
Name:Password: UserID:PrincipleGroup:Gecos: HomeDirectory:Shell

This what my username looks like in the file and I haven't done anything to it:
william:x:1000:1000:william,,,:/home/william:/bin/bash

---

### Post by jakihairi on 2007-06-28
thanks for the reply, i actually realize a moment ago that i could just boot into the recovery mode (which logs you in as root) and fix it from there. Once you hit escape at the grub screen and select the recovery mode option from the grub menu, you are logged in as root and 
```

usermod -G yourusername,adm,dialout,cdrom,floppy,audio,dip,video,plugdev,scanner,netdev,lpadmin,powerdev,admin yourusername

```
(substitute yourusername= the name you want to be an admin) will restore your admin priviledges and life goes on...

---

