---
title: "Can't update, missing one file."
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by geo_bio on 2006-08-28
I'm using Drapper Drake 6.06 right now.

I recently installed it, and it worked fine. I could get all 19 updates... Then I went to Windows XP, and used partition magic to move my partitions, including the Linux partition... Then it didn't load anymore, and I had to reinstall Ubuntu.

So I did. Now I'm using the reinstalled Ubuntu. I tried to update it, and it would read 18 of the 19 updates. This one won't work properly and the updater said: "Could not download all repository indexes".

[http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz)
That is the file that could not be found. However, if I go there, I can view the file perfectly fine.

Please tell me if there is a problem with my instalation and I should reinstall, or if I need to do something else first.

The reason I'm doing this is because last time I used the Add/Remove ... in the Applications menu and I could get the software I need. However, last time it didnt work until I updated. Now I think I have to update first before I can actually use the programs in there. I am also missing some of the pacakages that I saw last time in the list.

Please tell me if there is a problem with my instalation and I should reinstall, or if I need to do something else first. Thanks

---

### Post by Bachstelze on 2006-08-28
Try this :

backup your old sources.list

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```

edit it :

```
gksudo gedit /etc/apt/sources.list
```

delete everything so the file is blank, save the file, close gedit then run

```
sudo apt-get update
```

copy your old sources.list back

```
sudo mv /etc/apt/sources.list_backup /etc/apt/sources.list
```

Then run *sudo apt-get update* again and see how it works out.

---

