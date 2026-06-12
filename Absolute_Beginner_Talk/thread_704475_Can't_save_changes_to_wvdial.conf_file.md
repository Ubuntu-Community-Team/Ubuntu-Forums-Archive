---
title: "Can't save changes to wvdial.conf file"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by johnwen on 2008-02-22
I run wvdial and my modem is detected and am informed no phone number, password, and username is present.  I then went to "places" "computer" "file system" and navigated to the wvdial.conf in the /etc directory. After entering the required information I cannot exit and save the info. 

I'm informed I am not the owner and cannot write to it.  I tried changing permissions for the file and the folder but was denied. 

Thanks,
John


:guitar:

---

### Post by boblettoj99 on 2008-02-22
if you are using dolphin, highlight the file, then at the side there is a button which says edit as root. Thats what i use and it lets you save it!

good luck :D

---

### Post by OffAxis on 2008-02-22
You can also get to it from the command line as the super user (if you're not using dolphin)

```
sudo nano /etc/wvdial.conf
```

---

