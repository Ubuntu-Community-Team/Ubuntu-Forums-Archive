---
title: "Disc hog type of program/ script?"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by Stew2 on 2006-07-23
Hi all. Does anyone know of a program or script that will show you how big all your files are? I have used just over 18 gigs and the only large group of files I have on here are approx 5 gigs of music. Trying to figure out whats eating up the other 13 gigs. Not many pics or anything on it either. :confused: 

Regards,
Stew2

---

### Post by moma on 2006-07-23
$ cd $HOME

Show size of directories
$ du -h 

Show size of files
$ du -ha

For more info
$ man du
---------------------

Find all files >= 4Mb
$ cd $HOME
$ find . -size +4M
$ find . -name "*mp3" -size +4M -ls
----------------------

Or use Baobab (it will be incl. in Edgy Eft, next Ubuntu. You can apt-get it.)
[http://www.marzocca.net/linux/baobab.html]("http://www.marzocca.net/linux/baobab.html")

// moma
 [http://www.futuredesktop.com/ubuntu6.06.html]("http://www.futuredesktop.com/ubuntu6.06.html")

---

### Post by jayemef on 2006-07-23
I always recommend [FileLight]("http://www.kde-apps.org/content/show.php?content=9887") for tasks like this. It's a KDE app, but it's definitely worth it, as it gives you a nice pie-chart representation of whatever disk-space you want.

```
$ sudo apt-get install filelight
```

---

### Post by Stew2 on 2006-07-23
Thanks guys! :) I appreciate it. I looked on the internet but could only find windows apps. Thanks again!

Regards,
Stew2

---

### Post by Steveire on 2006-07-23
```

fsview /

```
Replace the '/' with whatever directory you want to start in and it'll give you a graphical view.

---

### Post by Stew2 on 2006-07-23
Hmmm... looks like the disc hog is my music. :) More on there than I thought!
Thanks again guys!

Regards,
Stew2

---

