---
title: "[SOLVED] copy a install disc."
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by matchstich on 2008-01-16
my question is:  how do i make a iso image of a disc i got from ship it?

i have gnomebaker installed. cept this all new to me.



thanks

---

### Post by hyper_ch on 2008-01-16
Dunno with gnomebaker, I normally use K3B. It's fairly simple there (I think it's also quite similar to Nero....). You may want to try with that.

---

### Post by kpkeerthi on 2008-01-16
Place the CD media in your drive. If it automounts, unmount using **sudo umount /dev/cdrom**. Then **dd if=/dev/cdrom of=cd.iso**.

---

### Post by sisco311 on 2008-01-16
i can't help you with gnomebaker but you can do it from a terminal.
unmount the cd/dvd:
```
**sudo umount /dev/cdrom**
```create the iso:
```
**dd if=/dev/cdrom of=file.iso bs=1024**
```
i am slow:)

---

### Post by matchstich on 2008-01-16
forgot to mention i have two burners . can i  copy the disc  from one 

to the other..?


thanks

---

### Post by sisco311 on 2008-01-16
i think you should try k3b.```
sudo aptitude install k3b
```

---

### Post by kpkeerthi on 2008-01-16
Yes you can. I remember brasero and k3b having the option to copy discs. Not sure about gnome-baker.

---

### Post by matchstich on 2008-01-16
hey y'all ,

thanks a lot for the info.

i installed both packages and will try them out this week end.

will get back and let you know how it came out.

---

