---
title: "help! can't login"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by blazini on 2007-11-06
I was downloading something and I guess I ran out of disk space, and my comp froze up. I hit the reset button, when I tried to login I got an error, something about couldn't load GDM cuz disk space is full. I booted the live CD but can't switch to my administrator accont to delete files. Is there a way to access administrator account or otherwise delete files on the HD with the CD?

---

### Post by Dr Small on 2007-11-06
When at the login screen, press CTRL + ALT + F1.
This will open Virtual Terminal #1.

Login via the command line, and then remove the file that eat up all of your disk space:
```
rm *filename*
```

Dr Small

---

### Post by Pumalite on 2007-11-06
Boot into Recovery and do it from there.(if you can)

---

### Post by blazini on 2007-11-06
> **Dr Small said:**
> When at the login screen, press CTRL + ALT + F1.
This will open Virtual Terminal #1.

Login via the command line, and then remove the file that eat up all of your disk space:
```
rm *filename*
```

Dr SmallOK, I did that, but every time I type the file location, it says "file not found". I'm starting with my home folder. I can't change directory (cd) either

---

### Post by blazini on 2007-11-06
> **Pumalite said:**
> Boot into Recovery and do it from there.(if you can)

how might I do that?

---

### Post by blazini on 2007-11-06
anybody? I have some things I really want to get done before bed that I can't get to on my windows drive.

---

### Post by blazini on 2007-11-07
bump, figured out the Grub recovery console but it's the same deal, can't find any filename I type.

---

### Post by blazini on 2007-11-07
Can anybody help? Like I said, using ctrl+alt+F1 gets me a "file does not exist" error no matter what Filename I type. I've tried  starting with the /home dir and even media/disk/home dir. the cd (change directory) command doesn't work either. The prompt  after login is <username>@<username>-desktop $:, (my actual admin username). Grub recovery console seems to be the exact same thing. I really need help with this. I'm typing from the live CD!!!

---

