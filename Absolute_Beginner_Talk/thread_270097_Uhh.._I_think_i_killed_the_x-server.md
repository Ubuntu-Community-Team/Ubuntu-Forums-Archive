---
title: "Uhh.. I think i killed the x-server"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by Enjeru on 2006-10-02
Ok well I've only recently gotten Ubuntu so I'm not too used to it.  I edited out 'wacom' from /etc/X11/xorg.conf because I thought it would let me run photoshoo 7.0 as it said on the wine websites:

[http://appdb.winehq.org/appview.php?iVersionId=1336](http://appdb.winehq.org/appview.php?iVersionId=1336)

is there ny way i can fix this because now my x-server will not start and im stuck in terminal which wont let me load the file through gedit to fix it...

---

### Post by jd65pl on 2006-10-02
If you didn't make a copy of xorg.conf that you can restore, start in recovery mode then do

```
sudo nano /etc/X11/xorg.conf
```

Unedit the line you edited out then do
```
sudo reboot
```

That should sort you out

---

### Post by arkangel on 2006-10-02
in /etc/X11/  you must have a backup  like xorg.conf.xxxx   just change the name , or if you remember what you did  undo it

---

### Post by Enjeru on 2006-10-02
i made a backup copy on my desktop called xorg.conf, what command do i need to use to replace that with the one in /etc/xll... please be specific in directions, i really have no clue what i am doing...

---

### Post by qamelian on 2006-10-02
> **Enjeru said:**
> i made a backup copy on my desktop called xorg.conf, what command do i need to use to replace that with the one in /etc/xll... please be specific in directions, i really have no clue what i am doing...

```
sudo cp ~/Desktop/xorg.conf /etc/X11/
```

---

### Post by jd65pl on 2006-10-02
Have a look at this thread it should help you restore from a backup

[http://ubuntuforums.org/showthread.php?t=258186]("http://ubuntuforums.org/showthread.php?t=258186")

---

### Post by Enjeru on 2006-10-02
ok thx guys i got it fixed... phew.. thought i was gonna have to reformat or something.. Thanks a lot :D

---

