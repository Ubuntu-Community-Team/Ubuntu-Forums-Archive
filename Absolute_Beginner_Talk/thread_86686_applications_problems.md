---
title: "applications problems"
date: 2005-11-06
forum: Absolute Beginner Talk
---

### Post by avenger on 2005-11-06
Hi, i recently encountered a rather pressing problem with ubuntu. As it seems that the media players that came with ubuntu doesn't seem to be able to play mp3 files i  went hunting for codecs. i stumbled upon easyubuntu and tried to install it. at the end of the installation i was told to goto applications--->add applications-->and install real player from there.
here comes the problem, when i start add applications , a message box containing the blow message appears
"Unable to get exclusive lock. this usually means that another package management application(like apt-get or apititude) already running. please close that application first."
as i dont remember running another package management application, nor can i find any running....i'm out of ideas. i tried shutting down and rebooting, but the problem still persists.
any help is appriciated

---

### Post by thinhlegolas on 2005-11-06
Try xmms, my favourite music player

Download the latest package from [www.xmms.org](www.xmms.org)

tar zvxf <filename>
cd <xmms folder>
./configure
make
make install

Make sure you do this before installation

sudo apt-get install build-essentials

---

### Post by thinhlegolas on 2005-11-06
If you still have problems, please post your problems here... regarding mp3 issues, most of the Linux distros doesn't have the built-in mp3 playing capability for users because of legal issues

---

