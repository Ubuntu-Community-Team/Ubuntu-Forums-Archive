---
title: "how to install gvidcap (to record screen video)?"
date: 2006-02-26
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-02-26
I got this error when xvidcap &... but  i couldnt install gvidcap (better program but not found in the repos) 

libpng.so.2  is the main error;

I try to install :
#!/bin/bash
apt-get -f -y install libavcodeccvs
apt-get -f -y install libavcodeccvs-dev
apt-get -f -y install libavcodec2
apt-get -f -y install libavcodec1-dev
apt-get -f -y install libavcodec-dev
apt-get -f -y install libavcodec2-dev

from:
## libavcodec1
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main

Not yet working ... packages not found ... 

Someone has an idea ?

Greetz

Patrick

---

### Post by patrick295767 on 2006-02-27
I dont know how to use gvidcap but I use now xvidcap:
  
How to Install It :
===========
  
(via script)
1/ First, get the file : xvidcap_1.1.3-1_i386.deb and copy it to /root

2/
```
#!/bin/bash
echo "  " >> /etc/apt/sources.list
echo "## libavcodec1 " >> /etc/apt/sources.list
echo "deb ftp://ftp.nerim.net/debian-marillat/ sarge main" >> /etc/apt/sources.list
apt-get update
##apt-get upgrade   # I consider you upgraded ur linux
apt-get -f -y install imagemagick
apt-get -f -y install libpng2
cd /root
dpkg -i xvidcap_1.1.3-1_i386.deb
echo "#!/bin/bash" > "/root/xvid.sh"
chmod +x /root/xvid.sh
chmod 777 /root/xvid.sh
echo "xvidcap --gui no --compress 9 --file ~/myvideo.mpeg --frames 0 --fps 10 --cap_geometry 1024x768+0+0" >> "/root/xvid.sh"
echo "if you wanna make a avi file of ur screen, run sh /root/xvid.sh" 
echo "u can move this little script, where you want & need"
echo "** Greetz' **"
```
  
3/ to record ur screen:
sh /root/xvid.sh
  
(rename the gz of the video to avi, once done)
(mplayer can play it)

Pat'

---

### Post by Craftycorner on 2006-12-10
Are these directions for Dapper Drake?

---

