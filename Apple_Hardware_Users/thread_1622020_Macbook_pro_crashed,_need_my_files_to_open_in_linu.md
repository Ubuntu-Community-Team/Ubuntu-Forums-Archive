---
title: "Macbook pro crashed, need my files to open in linux"
date: 2010-11-15
forum: Apple Hardware Users
---

### Post by superflychick on 2010-11-15
Hi, 

My macbook pro crashed this week, and I need to get to my files. So far, I have removed my HDD from the mac, put it in a external case, and plugged it into my other computer running linux. I can mount the HD, look around in it, but when I try to open my personal files (pics, word docs, etc) I get an error: "You do not have the permissions necessary to view the contents of "folder"" . 

I read another thread on this, but I am a linux newbie -- basically it would be nice to have a little clearer instructions (b/c I dont want to screw anything up), and an clearer idea of what the commands suggested actually do?

Here is a link to the thread I read earlier: 
[http://ubuntuforums.org/archive/index.php/t-852144.html](http://ubuntuforums.org/archive/index.php/t-852144.html)

Thanks

---

### Post by aysiu on 2010-11-15
> **superflychick said:**
> Hi, 

My macbook pro crashed this week, and I need to get to my files. So far, I have removed my HDD from the mac, put it in a external case, and plugged it into my other computer running linux. I can mount the HD, look around in it, but when I try to open my personal files (pics, word docs, etc) I get an error: "You do not have the permissions necessary to view the contents of "folder"" . 

I read another thread on this, but I am a linux newbie -- basically it would be nice to have a little clearer instructions (b/c I dont want to screw anything up), and an clearer idea of what the commands suggested actually do?

Here is a link to the thread I read earlier: 
[http://ubuntuforums.org/archive/index.php/t-852144.html](http://ubuntuforums.org/archive/index.php/t-852144.html)

Thanks
After mounting the hard drive, press Alt-F2

A "run" dialogue will pop up. In that dialogue, paste in the command ```
gksudo nautilus
``` Then look around and copy over your personal files.

---

