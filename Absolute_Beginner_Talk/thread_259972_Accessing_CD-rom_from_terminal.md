---
title: "Accessing CD-rom from terminal"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by calvinthomas on 2006-09-18
How can I access my cd-rom drive from the terminal?

Calv

---

### Post by Lord Illidan on 2006-09-18
Mount it first.

It depends on its physical location : /dev/hda /dev/hdb /dev/hdc whatever...

The format will be like this anyway. Check if you have a mountpoint for it in /media.

```
sudo mount /dev/hda /media/cdrom0
```
```
cd /media/cdrom0
```
```
ls
```

Now you can see what is inside the cd. Hope it is clear enough, if not..tell me...and I will clarify further.

---

### Post by calvinthomas on 2006-09-18
Thats perfect, thankyou!

Calv

---

