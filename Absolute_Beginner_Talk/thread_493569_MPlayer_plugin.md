---
title: "MPlayer plugin"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by boglio on 2007-07-05
I'm having some problems with the mplayer firefox plugin, i cant get it to work at all :( I'm running feisty 32bit and i did "apt-get install mozilla-mplayer" but i cant play any videos from [http://stage6.divx.com](http://stage6.divx.com) i just get a message "For Linux support try Mplayer." 

Thanks.

---

### Post by jrusso2 on 2007-07-05
in firefox type about:plugins in the address bar and see if you can see the mplayer plugin associated with what ever files you want it to play.

---

### Post by NeoLithium on 2007-07-05
Try doing: 
```

sudo aptitude remove totem-mozilla
```
And see if that will help after you restart firefox.  If the two plugins exist together, they figfht for the spot and don't work with either :)

---

