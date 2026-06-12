---
title: "Errors while downloading utorrent"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by God_of_Belac on 2007-06-09
I attempted to download utorrent, following the instructions here: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_use_.C2.B5Torrent_under_Wine](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_use_.C2.B5Torrent_under_Wine)

This is what happened:

[me]:~$ wget [http://download.utorrent.com/1.6.1/utorrent-1.6.1-install.exe--20:30:31--](http://download.utorrent.com/1.6.1/utorrent-1.6.1-install.exe--20:30:31--)  [http://download.utorrent.com/1.6.1/utorrent-1.6.1-install.exe](http://download.utorrent.com/1.6.1/utorrent-1.6.1-install.exe)
           => `utorrent-1.6.1-install.exe'
Resolving download.utorrent.com... 72.20.34.146
Connecting to download.utorrent.com|72.20.34.146|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
20:30:31 ERROR 404: Not Found.

Can someone tell me what I did wrong and how to fix it so utorrent downloads and works?

Thanks!

---

### Post by yurimxpxman on 2007-06-09
> **God_of_Belac said:**
> I attempted to download utorrent, following the instructions here: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_use_.C2.B5Torrent_under_Wine](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_use_.C2.B5Torrent_under_Wine)

This is what happened:

[me]:~$ wget [http://download.utorrent.com/1.6.1/utorrent-1.6.1-install.exe--20:30:31--](http://download.utorrent.com/1.6.1/utorrent-1.6.1-install.exe--20:30:31--)  [http://download.utorrent.com/1.6.1/utorrent-1.6.1-install.exe](http://download.utorrent.com/1.6.1/utorrent-1.6.1-install.exe)
           => `utorrent-1.6.1-install.exe'
Resolving download.utorrent.com... 72.20.34.146
Connecting to download.utorrent.com|72.20.34.146|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
20:30:31 ERROR 404: Not Found.

Can someone tell me what I did wrong and how to fix it so utorrent downloads and works?

Thanks!
Why don't you just use a different client, such as Azureus or KTorrent?

---

### Post by Rocket2DMn on 2007-06-09
It looks like the link it is trying to download from no longer exists, the tutorial could just be outdated now.
A lot of people, including myself, like Azureus for downloading torrents - it is java based and is therefore cross platform, meaning you can use it in Windows, Linux, or any other system that has the Java Virtual Machine.
There is no need to run torrents using a program under Wine when there are native programs for linux

---

### Post by just learning on 2007-06-10
try using this it worked great for me.news.softpedia.com/news/uTorrent-under-Ubuntu-in-3-Easy-Steps-49037.shtml.

---

### Post by zvacet on 2007-06-10
Download it from this site


[http://utorrent.com/download.php]("http://utorrent.com/download.php")

 (standalone version)and put it in any folder(let say  that folder name is programs just for example).


```
wine /home/username/programs/utorrent.exe
```

and you will have utorrent runing

---

