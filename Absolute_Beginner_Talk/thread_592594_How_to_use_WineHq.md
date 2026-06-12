---
title: "How to use WineHq ??"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by 3enith on 2007-10-26
How to install utorrent using Wine on ubuntu 7.04?i installed wine but can't find it.:confused:

---

### Post by rolodoom on 2007-10-26
You need to configure wine:

```
$ winecfg
```Then, you only should doble click on the *.exe (windows executable file) that you want to open, wait a little bit and then you should see a window just like if you were running it on a windows box. That´s how it works for me. I set configuration to windows 2000.

Maybe you could read this information at winehq website:
[http://www.winehq.org/site/docs/wineusr-guide/config-wine-main](http://www.winehq.org/site/docs/wineusr-guide/config-wine-main)

Hope it helps, but don´t know why you want to install a windows torrent client when there are a some good GNU programs, I use [deluge]("http://deluge-torrent.org/") and it works fine for me.

---

### Post by 3enith on 2007-10-26
hi thanks should i select win2000 too? is it works better than others?

---

### Post by rolodoom on 2007-10-26
Sometimes I've been having some trouble with wine using Xp configuration, so I almost use windows 2000 and works like a charm, but think that you should try yourself and see the results.

If something goes wrong you can delete the configuration folder at you home folder, think is .wine or something like that and run winecfg again and try again.

---

### Post by 3enith on 2007-10-26
thanks a lot I'll use deluge I didn't know this

---

