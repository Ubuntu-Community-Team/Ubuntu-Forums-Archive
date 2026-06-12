---
title: "Firestarter ?"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2006-06-15
Any way to get Firestarter to start automatically when I login ?  Thanks

---

### Post by r4ik on 2006-06-15
Try.

[http://www.fs-security.com/docs/](http://www.fs-security.com/docs/)

And read the FAQ.

Good luck.

---

### Post by noswal on 2006-06-16
Systems > Preferences > sessions > start up programs tab
edit in gksudo /usr/sbin/firestarter 

In firestarter perferences check start/restart on dial out or on whichever suits your connection

---

### Post by u.b.u.n.t.u on 2006-06-16
[QUOTE=Drakkor]Any way to get Firestarter to start automatically when I login ?  Thanks[/QUOTE]

Just an added note, firestarter does not start with the blue button next to the clock. It starts hidden. You can verify that it is working by:

 ```
sudo /etc/init.d/firestarter status
```

---

### Post by Drakkor on 2006-06-16
Thanks guys,got it. :D  I did try to RTFM, but it seemed very confusing to me.

---

### Post by u.b.u.n.t.u on 2006-06-16
[QUOTE=Drakkor]Thanks guys,got it. :D  I did try to RTFM, but it seemed very confusing to me.[/QUOTE]

Linux is not user friendly, but it is slowly getting there.

---

### Post by Drakkor on 2006-06-16
Having played with a 4 to 5 different Linux distros, I know Ubuntu could be a top
contender as far as a workable Desktop solution if one would put just a little time and effort in getting it to run how they want it. Trouble is too many people think it's like a car, turn the switch and it runs, and they don't need,or don't want to learn how an internal combustion engine works. I am now dual booting
Ubuntu and XP,though the only thing I would need XP for is to play some games.
**UBUNTU ROCKS !**  :D

---

