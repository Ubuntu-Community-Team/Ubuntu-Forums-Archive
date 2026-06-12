---
title: "where is the repository? i'm trying to install nvidia drivers"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by noktekniq on 2006-11-01
so i have a 7800gt and i'm trying or learning to to install the following stuff listed in this thread. 
[http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)
it tells me to add stuff in the repos. but where is that? how do i do that? someone please give me some tips. greatly appreciate it. first time ubuntu user. LOL

---

### Post by chuckyp on 2006-11-01
Perhaps check out help.ubuntu.com  but I believe the nvidia-glx package is in universe.   If you add universe and multiverse as repos your should be fine.   You can add these by going to System > Administration > Software Sources

---

### Post by Sef on 2006-11-01
> it tells me to add stuff in the repos. but where is that? how do i do that? 

Enabling the [repositories]("https://help.ubuntu.com/community/Repositories/Ubuntu").

[How to Install Anything]("http://monkeyblog.org/ubuntu/installing/") on Ubuntu.

---

### Post by NeoLithium on 2006-11-01
In a terminal window, type ```
sudo gedit /etc/apt/sources.list
``` and remove the # before the lines that start with 'deb'. That will enable the repositories, you may also want to add the word multiverse to the lines that simply are universe repositories, such as this: 
```

deb http://ca.archive.ubuntu.com/ubuntu/ dapper universe
should look like:
deb http://ca.archive.ubuntu.com/ubuntu/ dapper universe multiverse

```

---

### Post by noktekniq on 2006-11-01
all that is gonna take some serious readings. i think i'm gonna get that ubuntu book to read. to learn about this sucker.

---

### Post by NeoLithium on 2006-11-01
Those are actually handy to have; although, the most important thing with linux is to remember that you need patience and a willingness to learn with trial and error (Unfortunately, I had more errors than normal, but HEY!).  

One book that I have and enjoy, is Beginning Ubuntu Linux: From Beginner to Professional by Keir Thomas. It explains everything quite well, including absolute beginners.

---

### Post by noktekniq on 2006-11-01
is that book actually better then the one [http://product.half.ebay.com/Official-Ubuntu-Book-the_W0QQprZ52764647QQtgZinfo](http://product.half.ebay.com/Official-Ubuntu-Book-the_W0QQprZ52764647QQtgZinfo) called Official Ubuntu Book, the

---

