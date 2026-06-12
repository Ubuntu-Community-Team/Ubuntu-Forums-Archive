---
title: "Gecko media player for Ubuntu"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by DCboi on 2007-07-31
I was trying to install gecko-media player for Ubuntu from : [http://dekorte.homeip.net/download/gecko-mediaplayer/](http://dekorte.homeip.net/download/gecko-mediaplayer/) . 

They don't seem to provide binary for ubuntu. Does anyone know where I can find one ?

---

### Post by atomkarinca on 2007-07-31
you can download and manually install from the tar.gz file.

---

### Post by mcduck on 2007-07-31
You can get a .deb package from here: [http://www.getdeb.net/app.php?name=Gecko+Media+Player]("http://www.getdeb.net/app.php?name=Gecko+Media+Player")

---

### Post by dashnak on 2007-08-07
And how do you get firefox to use it?

---

### Post by DCboi on 2007-08-08
Package link provided by mcduck will be installed in firefox's plugin directory. So firefox will automatically pick them up.

---

### Post by dashnak on 2007-08-08
Not really... I used that package, but firefox doesn't use, it still uses mozilla-mplayer, and if I remove it, it uses nothing at all.....

---

### Post by jpmontalbo on 2008-01-04
I know this is an old thread but been using gecko-media-player for firefox and I like it. The reason why firefox won't utilize the plugins is because they are all installed in /usr/lib/mozilla/plugins by default rather than /usr/lib/firefox/plugins. All I did was symlink the files from the correct directory and it works. Another method is just copy all plugins from /usr/lib/mozilla/plugins to /usr/lib/firefox/plugins. Hope that helps.

---

### Post by z0mbie on 2008-02-28
The packages at getdeb were updated. Now it works without the need to copy plugins. See comments:
[http://www.getdeb.net/comment.php?rel_id=2214](http://www.getdeb.net/comment.php?rel_id=2214)

---

