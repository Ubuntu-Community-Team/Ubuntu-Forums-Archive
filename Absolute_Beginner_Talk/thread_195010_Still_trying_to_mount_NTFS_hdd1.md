---
title: "Still trying to mount NTFS hdd1"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by goodmore on 2006-06-12
Tried to follow this guide [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows), but when I get to sudo nano /etc/fstab my NTFS drive hdd1 is not listed please help.

---

### Post by taurus on 2006-06-12
Then use that guide and add an entry in /etc/fstab for your NTFS partition then!!!  I would look something like
```

/dev/hdd1 /windows ntfs nls=utf8,umask=0222 0 0

```
And of course, don't forget to create a /windows mountpoint as
```

sudo mkdir /windows

```

---

### Post by goodmore on 2006-06-12
Then use that guide and add an entry in /etc/fstab for your NTFS partition then!!! 


How do I do that ?


THANX

---

### Post by JanVH on 2006-06-12
[QUOTE=goodmore]Then use that guide and add an entry in /etc/fstab for your NTFS partition then!!! 


How do I do that ?


THANX[/QUOTE]

```
sudo gedit /etc/fstab
```

---

### Post by anaconda on 2006-06-12
Before editing fstab, you can try if it will work from terminal.

sudo mkdir /windows     (if you haven't created it yet)
sudo mount -t ntfs /dev/hdb1 /windows

after thet you should be able to access your windows drive from: /windows

If it worked, then edit the fstab, to make changes permanent

---

### Post by goodmore on 2006-06-12
All is well thank you. I was able to make it work thanx to the help here.

---

