---
title: "Mount to /home"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by poordamnedfool on 2007-10-16
When i reinstalled ubuntu today i decided that i wanted to mount my media drive to the home folder now instead.  it is currently mounted as /media/sdb1, and i want it to become the new /home, the problem is that i do not want to loose any of the files that i currently have on /media/sdb1.  how would i go about doing this?

thanks 
jon

---

### Post by LowSky on 2007-10-16
you would need to repartion it. beside your current /home folder has all of your installed programs on it, they are just hidden

---

### Post by maybeway36 on 2007-10-16
No... Installed programs are in /usr.

---

### Post by poordamnedfool on 2007-10-16
Thats what i thought, i was hoping that there would be some way i could copy my current home directory and then paste it into the new one, guess not... ok thanks

---

### Post by poordamnedfool on 2007-10-16
would i be able to move sdb1 into the home directory as /home/downloads?

---

### Post by maybeway36 on 2007-10-16
I think some kind of cp might work. Try:
```
cp -r /home/* /media/sdb1/
```
This should copy everything in /home to /media/sdb1.

---

### Post by jr.gotti on 2007-10-16
I believe the correct way to do this would be do run a

```

sudo mount /media/sdb1 /home

```You could also add it to /etc/fstab to have it mounted upon boot.

---

