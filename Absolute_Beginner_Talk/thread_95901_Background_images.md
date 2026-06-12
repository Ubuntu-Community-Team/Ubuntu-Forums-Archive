---
title: "Background images"
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by xbeatnickx on 2005-11-27
Hi all,
When I try to use background images from /media/windows - the swap partition,  the file browser sees the files, extensions .bmp and .jpg, but it says they are 0 pixels x 0 pixels. However, when I view them through filebrowser only and not through the change background option then I can view them. 

Might this have to do with the mount option I am using for this drive? I switched  from using ... -o umask=0 to -o umask=000

Any thoughts?

---

### Post by ssam on 2005-11-27
can you copy the images to your home folder and then see if it works.

quick note on terminology: in unix the swap partition is the virtual memory partition (yes i know its a silly name). /media/windows would just be your your windows partition. (atleast you aren't calling them by windows drive letter :-) )

---

### Post by xbeatnickx on 2005-11-28
I copied the images to  /usr/share/background but something strange happened. The image files still came up empty. The file sizes showed up normal but when I tried pulling up the images nothing happened and when I went into windows and it tells me that the files have been corrupted. I am thinking that it has something to do with dropping and dragging from the Cruzer Micro. Anyone else have the problem?

---

