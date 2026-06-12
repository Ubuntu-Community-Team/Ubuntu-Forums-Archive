---
title: "Aaarhg! Widescreen 1280 x 800 in Acer Aspire 5670"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by kuahyeow on 2006-11-16
Hi, after looking at various threads here, none of them really works. I've tried 

sudo dpkg-reconfigure xserver-xorg

and following all the questions there. no luck, my choices are still limited to 1024x768, 800x600, and 64x800.

Adding a modeline in the monitor section (as per running gtf in terminal) does not work either.

Any ideas on how to make this work?

thanks in advance.

---

### Post by kuahyeow on 2006-11-16
In fact, trying to change the resolutio to anything other than 1024x768 crashes Xserver.

---

### Post by kuahyeow on 2006-11-16
Yah! After more searching, some forum told me that i needed drivers, so another search turned up this very reliable page:

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_1:_Installing_Dapper.27s_Included_Driver_.288.25.18.29](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_1:_Installing_Dapper.27s_Included_Driver_.288.25.18.29)

And it's done :)

---

### Post by scifan2 on 2007-01-24
Try the instructions in this thread for how to build the deb's and install them for Edgy.

(These work, I have used them on my 5670)

[http://www.ubuntuforums.org/showthread.php?t=321766](http://www.ubuntuforums.org/showthread.php?t=321766)

Note that Beryl and XGL seem rather unstable on my box... hopefully that will improve though as they are pretty cool... :)

---

### Post by Mba7eth on 2007-01-24
I had the same problem on Dell inspiron 640m 
I tryed 915 resolution and everything worked fine . 

try it !! 
1.first expand ur source.list as follows 
```
$gedit /etc/apt/source.list
```
remove every # from a non-commet line 
2.
```
$sudo apt-get update
$sudo apt-get install 915resolution
```

Hopefully it will work :-\"

---

