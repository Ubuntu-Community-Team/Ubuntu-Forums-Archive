---
title: "Ndiswrapper Error"
date: 2007-12-22
forum: Apple Intel Users
---

### Post by Stu09 on 2007-12-22
I have been following the MacBook wiki to install Gutsy onto my Black C2D Macbook.

I am getting this error when trying to setup ndiswrapper The wiki specifies Ndiswrapper-1.8 but I found that only version 1.9 was available.

> stuart@Macbook:~$ sudo ndiswrapper -i "~/atheros/net5416.inf" 
installing net5416 ...
couldn't open ~/atheros/net5416.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 181.
stuart@Macbook:~$ sudo ndiswrapper -l
net5416 : invalid driver!

Help!

---

### Post by Stu09 on 2007-12-23
Well after much mucking about, I seem to have gotten past this hurdle.
Now I'm not able to load the module with modprobe.
See here [http://ubuntuforums.org/showthread.php?t=417731&page=9](http://ubuntuforums.org/showthread.php?t=417731&page=9)

---

### Post by Stu09 on 2007-12-23
So I discovered that typing 
```
sudo ndiswrapper-1.9 -i net5416.inf
```
actually seems to have installed the driver. Rather than typing * sudo ndiswrapper -i net5416.inf*
I don't know if this is correct, but it looks like it worked. I am still not able to load the module with modprobe.

Should I try and use madwifi instead ?

---

### Post by Rog-Mahal on 2007-12-24
I recommend using madwifi. Depending on what generation Macbook you have, you may need to download and install the bleeding edge source as opposed to using the package, I can help if you need to. I used the madwifi drivers and I've had no problems with them so far.

---

### Post by Stu09 on 2007-12-25
Yep. Thanks Rog.
I tried out madwifi and it worked straight away. :)

---

