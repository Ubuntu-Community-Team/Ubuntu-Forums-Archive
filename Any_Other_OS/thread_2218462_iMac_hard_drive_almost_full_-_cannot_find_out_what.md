---
title: "iMac hard drive almost full - cannot find out what takes up space"
date: 2014-04-20
forum: Any Other OS
---

### Post by vacco on 2014-04-20
I'm trying to clean up the hard drive on an old mac. Using command+i on Macintosh HD reveals that around 130 GB of the 160 GB partition has been used. Using command+i on the four folders in / returns a total of only about 15 GB. Now, what really boggles my mind is that even after turning on display of hidden files and folders, the grand total only increases by 1-2 GB. I've tried the advice I've found via Google and installed Omnidisksweeper, but still can't find anything. Interestingly enough though, Omnidisksweeper displays Macintosh HD as appx. 16 GB (seems to fit with the total size of all files and folders that I can find). I am really, really wondering what could be taking up the remaining 110+ GB on the hard drive.

Late 2006 2.16 GHz iMac (last white version)
OS X 10.6.8
Omnidisksweeper 1.7.2

---

### Post by mips on 2014-04-21
From you / (root) folder do 

```
df -h
```

```
du -sh *
```

[http://www.maclife.com/article/columns/terminal_101_managing_disk_space](http://www.maclife.com/article/columns/terminal_101_managing_disk_space)

---

### Post by bapoumba on 2014-04-21
You can give Onyx a shot [http://www.titanium.free.fr/downloadonyx.php](http://www.titanium.free.fr/downloadonyx.php)

---

