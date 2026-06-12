---
title: "Finding Installed Programs From Terminal"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by lunchbox1492 on 2006-10-03
I recently installed bittorrent using the terminal. Now I cant find where it went to. I am currently using the latest version of xubuntu if it helps. Help would be greatly appreciated.

---

### Post by annda on 2006-10-03
you can find it with the whereis command

more files will be found by locate

---

### Post by taurus on 2006-10-03
```
sudo find / -name *torrent -print
```

---

### Post by kerry_s on 2006-10-03
You can use locate, but you need to run updatedb first.

sudo updatedb
locate (filename)

---

### Post by bodhi.zazen on 2006-10-03
I always like learning alternates and enjoyed the above suggestions.

I use which.```
which bittorrent
```

---

