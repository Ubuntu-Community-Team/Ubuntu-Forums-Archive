---
title: "How do i tell wget to jump every 3 pages?"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by hopelessone on 2008-03-16
Hi,

wget -rl1 --cut-dirs=5 -U Mozilla ]http://web.archive.org/web/*sr_[COLOR="Red"]9[/COLOR]1nr_30/http:whatever.com

see the red 9 well i wanna increment +3 from there ... so the next is 12,15,18,21...etc all the way to 96

how can i do this?

thanks :)

---

### Post by yabbadabbadont on 2008-03-16
Here is a simple bash shell script that will do it for you.  You can either make it executable and then run it directly, or invoke it from your current shell inside of a terminal window.

i.e.
```
chmod 755 go.sh
./go.sh
```
or
```
. ./go.sh
```

---

