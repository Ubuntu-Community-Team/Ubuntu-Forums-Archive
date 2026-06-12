---
title: "how to mount / connect an ipod?"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by shutupimpoor on 2006-05-22
sometimes when i restart my computer I cannot access my iPod, and it is just charging. It acts as if it has been "ejected" in windows terms (sorry im new to linux). I always play my music through Banshee, but it doesn't recognize the ipod every now and then and its annoying turning off the computer to get it to recognize my ipod.

any suggestions?

---

### Post by xyz on 2006-05-22
Hi-
I'm really no expert at this but I took a look at this:
[http://ubuntuforums.org/showthread.php?t=144341&page=3&highlight=iPod](http://ubuntuforums.org/showthread.php?t=144341&page=3&highlight=iPod)
ans as a noobie, you may find it useful to read. I'm not certain it'll solve your particular problem; however, there's lost of Banshee-related stuff. Good luck.

---

### Post by Ecthelion on 2006-05-22
When your ipod is just charging, does it figure in mtab?
```
gedit /etc/mtab
```

And what is your fstab?
```
gedit /etc/fstab
```

Just an idea, but if it figures in fstab and not in mtab, you could try
```
sudo mount -a
```
And then it should be accessible i think.

---

