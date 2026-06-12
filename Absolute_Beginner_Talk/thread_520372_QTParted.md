---
title: "QTParted"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by colinireland on 2007-08-08
Hello,

I am having trouble partitioning my harddrive. I have installed QTParted but it only works under the root user. I tried logging in to the root account but my mouse will not work. I have since been advised by other people on a different thread that logging into the root account can cause problems. 

Does anyone know of a way to start QTParted from the command line?

Regards,
Colin

---

### Post by forestpixie on 2007-08-08
I'm guessing that it will only work with root - I've used GParted though so not sure.

To run from the terminal 

```
gksudo qtparted
```

 I don't know if you can boot with QParted - if you download GParted you can burn it as an .iso and boot with it


[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

---

### Post by AlexenderReez on 2007-08-08
try to use gparted...in terminal



> sudo apt-get install gparted

open with 

> gksudo gparted

surely you need to use super user mode to manage your disk,because if not other people can easily destroy/format your partition ...it is quite dangerous but use it carefully ... :)  

you can try livecd for that....most user will recommend you gparted livecd but give a try [parted magic]("http://news.softpedia.com/news/Parted-Magic-1-8-Available-Now-61073.shtml")

---

### Post by ZipoTe on 2007-08-08
Yeah! gparted live CD is my tool when i have to play with partitions on new computers. I recommend you to burn it by the case. It's really useful :D

---

### Post by colinireland on 2007-08-09
thanks for the help guys. im new to linux so if i run into any problems with the partitioning is it cool if I sent one of you a private message?

---

### Post by MenZa on 2007-08-09
No, post in the thread. That way, others reading the forum later with the same problems might not need to post. :)

---

