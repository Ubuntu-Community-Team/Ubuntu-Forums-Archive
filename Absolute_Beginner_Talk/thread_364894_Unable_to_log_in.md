---
title: "Unable to log in"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by hanksterling on 2007-02-18
I have been away for awhile. Last time I was working on my computer I was trying to install 6.10. I couldnt get it to boot up. Removed my old ati vid card and went with onboard video(Dell 800M). Whamo! Things are crusing along and I got to the log on screen, and it is asking for a username/password. Now Im not sure if I selected one in the install, but if I did I dont remember it. Can anyone suggest a way to change username/password?

---

### Post by taurus on 2007-02-18
Boot into the recovery mode from GRUB menu and paste the output of this command here.

```
ls -la /home
```

---

### Post by hanksterling on 2007-02-18
drwxr -xr -x 3 root root 1024 jan 6 16:35 (.)
drwxr -xr -x 21 root root 1024 jan 6 16:03 (..)       (blue text)
drwxr -xr -x 2 hank hank 1024 jan 6 16:35 (hank)

---

### Post by taurus on 2007-02-18
Is it hank or is it (hank)?  

Your log in name is probably hank then.  Now, you need to change the password to something you can remember.

```
passwd hank
```
Reboot and see if you can log in as hank with the new password.

```
shutdown -r now
```

---

