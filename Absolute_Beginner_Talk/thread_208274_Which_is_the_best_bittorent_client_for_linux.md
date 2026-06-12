---
title: "Which is the best bittorent client for linux?"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by FuzZy2006 on 2006-07-03
Which do you consider the best bittorent client for linux. Azureus is for proffesionals, BitTornado uses a big amount of my processor and can't run multiple torrents, and BitTorrent doesn't have any extra functions. I preffer to set the file priority (especially when i download big torrents with many files) and to see what's happenning (info about the other peers and so on. In Windows i used uTorrent.

---

### Post by Jagot on 2006-07-03
uTorrent is certainly very impressive in Windows.  Personally I use Azureus in Linux.  If you're a fan of the Opera browser then the latest version of that has a bittorrent client built in as well.

---

### Post by bohboh on 2006-07-03
I used to be a utorrent fan in xp, since moving to ubuntu i find ktorrent does the job

---

### Post by nzgreen on 2006-07-03
I like rTorrent.  It's an ncurses client.  I run it in a screen on my mythtv box.  Using sshfs I can now download .torrent files straight from my browser to that box.

Only "problem" I've found with it is it can kill my connection when uploading too fast - so much so that it affected my download speed.  I've set the upload rate limit to about half of my actual bandwidth and can now download at full speed.

---

### Post by ericesque on 2006-07-03
there is a tut floating around on how to get uTorrent working under linux.  I don't recall if it's using wine or not.  But perhaps a search will provide some help.

---

### Post by ericesque on 2006-07-03
yup  here's  thread that helps you set it up in wine [http://www.ubuntuforums.org/showthread.php?t=191161&highlight=uTorrent+linux](http://www.ubuntuforums.org/showthread.php?t=191161&highlight=uTorrent+linux)

uTorrent has been a long standing favorite of mine.

---

### Post by bohboh on 2006-07-03
I tried that tutorial a while ago and it sends my processor usage to near 100%. Not sure if it was me doing something wrong but i am sure i followed the tut exactly.

---

### Post by Winblowz on 2006-07-03
I prefer KTorrent, but I also use Azureus. If you need a lot of features, then you can't go wrong with Azureus, but if you want something simple that doesn't hog your CPU, then KTorrent would work better.

---

### Post by hikitsu4 on 2006-07-03
Rufus is also a very good programs looks almost exactly like utorrent and is opensource and fast. The problem is that it is made in python it takes about 45% cpu for me, with utorrent it is about 8-10%. (filename rufus_0.6.9-0ubuntu1_i386.deb).

rtorrent is made in c++ and uses libtorrent so it is fast and very resource friendly it just that rtorrent_0.5.3-1_i386.deb and libtorrent7_0.9.3-1_i386.deb cannot be installed in dapper 6.06 LTS it needs a newer libc6. But you can get an older version from the ubuntu resp.

There is also bittornado but that is made in python also and takes much cpu also, but user frendly and pretty fast.

ktorrent is made in c++ like rtorrent, and is resource friendly.

---

### Post by FuzZy2006 on 2006-07-03
I'd like to give a try to Ktorrent cos it is for linux. I preffer the latest version (KTorrent 2.0beta1) rather than the one from Synaptic. I downloaded the deb file and when i try to install it it says so : ```
trying to overwrite 'usr/share/mimelnk/application/x-bittorent.desktop'    ......     Errors were encountered while processing the file
```

---

### Post by Winblowz on 2006-07-03
You must use the --force-overwrite option...
```
sudo dpkg -i --force-overwrite "package name"
```

---

### Post by FuzZy2006 on 2006-07-03
thx a lot

---

