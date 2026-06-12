---
title: "I cannot access my NTFS drive"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by Sinaduel on 2006-09-09
well, I just recently had a computer meltdown, but, I still have all my music, video, and pic files on another hard drive, bad thing is, is it is NTFS, I was wondering, how do I go about getting those files, and putting them on my new drive. Please help.

---

### Post by RobsterUK on 2006-09-09
If you click on Places > Computer can you see your NTFS drive listed? If so try double clicking on it.

---

### Post by taurus on 2006-09-09
You need to edit your /etc/fstab and mount your NTFS drive...

```
gksudo gedit /etc/fstab
```
Then, add the following line to the end of /etc/fstab, assuming that your NTFS is on /dev/hda1!!!

```

/dev/hda1   /media/windows   ntfs   defaults,umask=0222   0   0

```
Save it and then run these two commands to mount it.

```

sudo mkdir /media/windows
sudo mount -a

```

---

### Post by Sinaduel on 2006-09-09
Yes I can see my drive listed, and when I tried the first code, it said "Gtk-WARNGING **: cannot open display"

When I double click on the drive it gives this
error: device /dev/hdb5 is not removable

error: could not execute pmount

---

### Post by taurus on 2006-09-09
Instead of running "gksudo gedit /etc/fstab", why don't you run this one then!

```
sudo nano /etc/fstab
```

---

### Post by Sinaduel on 2006-09-09
well, I did all that and it came up with this as an answer

error: device /dev/hdb5 is not removable
error: could not execute pmount

---

### Post by Sinaduel on 2006-09-09
thankyou, I got it all to work thankyou so much, thankyou.

---

### Post by taurus on 2006-09-09
> **Sinaduel said:**
> thankyou, I got it all to work thankyou so much, thankyou.
So now you owe me a beer!!!  ;)

---

