---
title: "How change permissions: ext3 usb drive?"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by halfB on 2007-06-09
I had a fat32 usb drive that would not automount on laptop (did on desktop.) So reformatted to ext3. Now it automounts but I do not have permissions to read  / write.  
1.  I have tried some recommeded chmod commands without effecct.
2. I have tried the Properties->Permissions after right click on drive icon, but they are greyed out and cannot be changed.
3. I do not understand if this can be changed using Administration->Users and Groups
What should I do to change permissions??????
Thanks 
halfB

---

### Post by halfB on 2007-06-09
If it would help, here is the ls -/a /media line dealing with this drive (named Seagate120.)

drw-rw-r--  3 root root 4096 2007-06-09 03:51 Seagate120


thanks
halfB

---

### Post by bodhi.zazen on 2007-06-09
What commands exactly ?

Assuming you are mounted at /media/Seagate120 :

```
sudo chown root.users /media/Seagate120
chmod 660 /media/Seagate120
```

Or you can 666 that last command. 777 = rwx (x = execute)

In fstab, add users to the options :

/dev/sdxx /media/Seagate120 ext3 **auto,users,...**  0 0

---

### Post by halfB on 2007-06-09
bodhi.zazen
Regrets that do not recall exactly what commands I used.  What you have written looks right.
There is no entry in my /etc/fstab for the sda1 or seagate120 drive.
What I did do was sudo nautilus.
Then went to the Seagate120 drive and was then able to change permissions.
Now the drive allows read and write access.
Thanks for your effort.
HalfB

---

