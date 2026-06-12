---
title: "how to host a video website on ubuntu"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by drarncruz on 2008-03-27
Hello guys and gals,
I recently installed a fresh copy of ubuntu desktop and XAMPP.  I also purchased a program called clipshare 2.6 pro to host a video website at home.  If anyone has tried to install this program and or the following programs to make clipshare work - please advise me on how to do this or direct me to any tutorials for this program.  The company that produces this script will install the program for $25 but I would like to know how to install it myself.
Linux Server (some old distributions are not supported) 
Apache Web Server 
MySQL (version 4 +) 
PHP (version 4.3 + / not tested on PHP 5) 
PHP Configuration
safe_mode = off 
max_execution_time = 1000 (recommended to prevent timeouts during video upload/conversion) 
session.gc_maxlifetime = 14000 (recommended to prevent session expires during video upload) 
open_basedir = (no value) 
output_buffering = on 
upload_max_filesize = 100M (recommended maximum video upload size in MB) 
post_max_size = 100M (recommended maximum video upload size in MB) 
GD Library 2 or higher 
Mplayer + Mencoder ([http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)) 
Flv2tool ([http://inlet-media.de/flvtool2](http://inlet-media.de/flvtool2)) 
Libogg + Libvorbis ([http://www.xiph.org/downloads](http://www.xiph.org/downloads)) 
**LAME MP3 Encoder** ([http://lame.sourceforge.net](http://lame.sourceforge.net)) 

Thanks everyone for your help - Go Ubuntu!!

---

### Post by Hospadar on 2008-03-27
all those prerequisites are available from the repositories, System->Administration->Synaptic

How exactly do you want to host these videos?  You may want to look into converting them to flash videos youtube-style even if you don't just use youtube, there are tools to make flash videos like that which I believe are free), it's a little more cross-platform friendly.

---

### Post by drarncruz on 2008-03-28
I guess the site i'm a trying to host would be like youtube.  I just want to see if the script even works.  I will try the repository and see if I can install all the programs.  Do you know if there is a way to reverse these changes if they don't work correctly?  Is there a "restore" feature on ubuntu?
 Thanks for your guidance.

---

