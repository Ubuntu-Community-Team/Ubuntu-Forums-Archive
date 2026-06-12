---
title: "uvcvideo driver"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by Luther786 on 2007-08-13
I am attempting to get a Logitech QuickCam Pro 5000 Webcam to work with Ubuntu 7.04.  I have had no success.

I put in the following, Code:
svn checkout [http://svn.berlios.de/svnroot/repos/linux-uvc/](http://svn.berlios.de/svnroot/repos/linux-uvc/)
cd linux-uvc/linux-uvc/trunk
make
sudo make install

It installs and looks pretty such that I end up with

:~/linux-uvc/linux-uvc/trunk$

According to other posts on here then when I plug in the camera it should be recognized, but nothing happens when I plug in the camera

I was looking at the wiki for this driver to get it to work and I also am completely confused on how to get/use luvcview for the camera (here's the link: [http://openfacts.berlios.de/index-en.phtml?title=Linux+UVC](http://openfacts.berlios.de/index-en.phtml?title=Linux+UVC))
Specifically on the wiki it's this part that confuses me
" Applications
luvcview
To test UVC luvcview is recommended. Take a look at the readme file for all options. This package can helps others to write software basing on his released source-code.

   1. Download the latest luvcview-*.tar.gz
   2. Install SDL development packages for your distro (e.g. Debian needs libsdl1.2-dev and a million automatically installable prerequisites)
   3. Unpack the sources run make 

If the image is bad try clicking the 'reset to default' button on luvcview. "

I am pretty sure other people have had this problem... and I hope they have resolved it too :)

---

### Post by Luther786 on 2007-08-13
.

---

