---
title: "stop an svn server"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by The Titan on 2008-03-09
i have started an SVN server with 
```
svnserve -d -r/srv/svn
```and now i cant figure out how to stop it.. I know... Im an idiot:lolflag:

EDIT: NOTE: I have done about 20 different google searches trying to figure this out

---

### Post by glennric on 2008-03-09
You could use
```
killall svnserve
```

---

### Post by The Titan on 2008-03-09
> **glennric said:**
> You could use
```
killall svnserve
```
wow.  Thanks, very easy.

---

### Post by kaens on 2008-03-09
You could do a
```

kill `pgrep svnserve`

```

or, if that fails

```

kill -9 `pgrep svnserve`

```

Be forewarned that the latter will stop svnserve in its tracks, and may be dangerous if it's doing stuff when you kill it.

---

