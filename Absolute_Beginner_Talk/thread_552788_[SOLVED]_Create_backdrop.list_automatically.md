---
title: "[SOLVED] Create backdrop.list automatically"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by High Camp on 2007-09-16
Hi All

I have created a cron job that changes my desktop background every 5 minutes (I'm running Xubuntu). I have also created a folder called .pics in my home directory where I am storing all of my desktop pics. I am constantly adding and subtracting from this folder. Is there any way to build a list of the files in the folder and use that list as backdrops.list? Something along the lines of a shell script that would get the complete file path for each file in a folder and output those paths in a .list document.

Thanks, I hope I explained that coherently.

---

### Post by High Camp on 2007-09-19
Hi All

This is partially a bump and partially more info. I have done more research and testing and what I have done so far is write a shell script that has this in it:
```
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

dir /home/simon/.pics/ >test.list
```

What this does is output a file called test.list with the following contents:
```
14,411\ Feet.JPG		 linux-logo.gif
1967Firebird03172007C.gif	 lion1.jpg
29sedan.gif			 lion2
35_Sedan.gif			 lion3
36ChevyLarge.gif		 lucifer-decal-black_LRG.gif
arg_hott_rodd_url.gif		 Marble1.jpg
arg-nomad-70-tr-url.gif		 Marble3.jpg
backdrops.list			 Marble6.jpg
beetle.gif			 n81006847_34480501_2023.jpg
cheetah1			 Om\ Mani\ Padme\ Hum1.gif
Creekrat04232007A.gif		 P1020198.JPG
Creekrat05082007A.gif		 P1020210.JPG
D.C.\ Route\ Mount\ Rainier.jpg  P1020213.JPG
dir.sh				 Photo_051107_001.jpg
DSCN0343.jpg			 ppe.gif
DSCN0357.jpg			 R004-007.JPG
DSCN0359.jpg			 rodkulture2006_LRG.gif
DSCN0364.jpg			 skull.gif
Good\ Morning.JPG		 T004-017.JPG
HenselWheelie.gif		 T004-019.JPG
hot_roc_cartoons_nov67.gif	 test.list
IMGP3304.jpg			 test.txt
IMGP3318.jpg			 Waddington\ 600.jpg
IMGP3331.jpg			 w-black-1_LRG.gif
linux-logo.2.gif

```

This is absolutely perfect and exactly what I want except for the formating. Because the files names are two on a line the XFCE desktop can't read the file names to use them as backdrop photos. Is there anyway to change this output?

Thanks much for any help,

---

### Post by typo101 on 2008-03-06
This might be a little late for a response. Surprise nobody else has chimed in.

Sound like "find" is what you want, not dir.

find /home/simon/.pics/ | grep jpg > test.list

---

