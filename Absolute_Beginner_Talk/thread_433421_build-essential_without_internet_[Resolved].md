---
title: "build-essential without internet [Resolved]"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by RedViking on 2007-05-04
I have no internet connection on the computer with Ubuntu (stupid, I know, but I'm not willing to pay the $80 to change that).  Most of the time, I'm fine and I can download any progams or updates I need with my laptop and then transfer them to my Ubuntu desktop via flash drive.  Obviously the build-essential command won't work with my XP laptop though.  Is there a place I can download that stuff with my laptop and then transfer it to my desktop later?  

I thought about using the build-essential command with the live cd in my laptop, but then I realized (1) I don't know if that will even work since it's not installed, and (2) where does that stuff go and how can I transfer it to the other computer?  

Any solution would be nice.  Thanks!

---

### Post by zvacet on 2007-05-05
You have build-essential on CD.

```
sudo apt-cdrom add
```

```
sudo aptitude install build-essential
```

---

### Post by aysiu on 2007-05-05
You're missing a [terminal](http://www.psychocats.net/ubuntu/terminal) command in there, zvacet: ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by RedViking on 2007-05-05
Thanks!  That helps a lot!

---

### Post by medya on 2007-05-05
[AptOnCD]("http://blog.shevin.info/2007/04/backup-your-installed-programs-on.html") is what you are looking for ! you can move insatlled programs on a ubuntu pc with internet to another ubuntu pc

---

### Post by aysiu on 2007-05-05
> **medya said:**
> [AptOnCD]("http://blog.shevin.info/2007/04/backup-your-installed-programs-on.html") is what you are looking for ! you can move insatlled programs on a ubuntu pc with internet to another ubuntu pc
That's a great thing, but in this case *build-essential* is already on the regular Ubuntu CD.

---

### Post by zvacet on 2007-05-05
What can I say?My mistake.Good point.

---

