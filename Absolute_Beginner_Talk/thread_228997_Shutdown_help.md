---
title: "Shutdown help"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by The_Shady_1 on 2006-08-03
2 questions:
1) I'm missing the shutdown,sleep,and restart buttons out of the shutdown menu.

2)I've installed KDE via: sudo aptitude install kubuntu-desktop
and tried to remove it via: sudo aptitude remove kubuntu-desktop

but yet when I start up I see Kubuntu.

I was looking to try KDE, but it appears to be more of a pain.

Thanks in advance

---

### Post by exgsr on 2006-08-03
I'm missing the same things also!
**missing the shutdown,sleep,and restart buttons out of the shutdown**

however, mine happened after i click to download latest update from  ubuntu.
and i'm running dapper gnome.


help help.. ](*,) 
the shutdown, restart button have been replace by one BIG hibernate button!

---

### Post by OU812 on 2006-08-04
I think I've seen this issue in other threads, so please check the forums. In the meantime, you could do either of these from a terminal

To shutdown
```
sudo shutdown now
```

To reboot
```
sudo reboot
```

john

---

### Post by exgsr on 2006-08-04
[SIZE="5"]SOLVED![/SIZE]

do the opposite of everything suggested here:
[http://ubuntu.wordpress.com/2006/03/20/disable-shutdown-for-normal-users/](http://ubuntu.wordpress.com/2006/03/20/disable-shutdown-for-normal-users/)

**But** keep in mind when editing **/etc/X11/gdm/gdm.conf** if [COLOR="Blue"]**/etc/X11/gdm/gdm.conf-custom**[/COLOR] exist thats the one should be edited. As the original gdm.conf will be ignored.

hopefully this will help somene. =;

---

### Post by vayde on 2006-08-05
Didn't work for me.  I have suspend, hibernate, restart, shutdown available when I push the red 'power' button if Im in a normal gnome session.

I have suspend and hibernate only when in xgl.

---

