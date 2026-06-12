---
title: "[SOLVED] bittorrent"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by colddayinapril on 2007-06-27
so, i was downloading a torrent, when i had to reboot to finsh something i was doing. when the system comes back up, my torrent is no where to be found. the file is still there, incomplete on the desktop, but nothign else. i can't seem to find the bittorrent application.  I tried installing the gui through synaptic, but that did'nt work either.

is there any way i can resume an interupted download and/or open bittorrent and change the settings?


[edit]

i'm also having a problem where i can't download multiple torrents. is says that it "can't listen - 98 already in use"
i am behind a router, but i never had this problem in XP

---

### Post by RomeReactor on 2007-06-27
Hi. Did you download the **.torrent** file to start the download? IF so, then just double-click on it and the download will resume.

As for the **"can't listen - 98 already in use"** problem, look [here]("http://ubuntuforums.org/showpost.php?p=2649719&postcount=3").

---

### Post by Golyadkin on 2007-06-27
Make sure to select the same download destination again, otherwise it will start again from scratch. It won't overwrite, it will first check the existing files and then it knows what is left to download.

---

### Post by Golyadkin on 2007-06-27
> **colddayinapril said:**
> 

i'm also having a problem where i can't download multiple torrents. is says that it "can't listen - 98 already in use"
i am behind a router, but i never had this problem in XP


This may be if you run multiple programs in Ubuntu to download multiple torrents. (one program per torrent) Only one program can listen to a specific port at the same time. In Windows you probably used a single program to download several torrents, like Azureus, BitComet or uTorrent. There are two solutions: specify a different port for each instance of the program you run, or use a torrent downloading program that supports multiple downloads. For examples Azureus for Linux, or uTorrent running with wine.

---

### Post by colddayinapril on 2007-06-27
juat installed Azureus. it's working fine and seems to have taken care of everything.

---

### Post by Golyadkin on 2007-06-27
Yup, thats what I thought :) Nice to hear it worked. You can edit your first post in this thread and change Thread options to set it as "Resolved".

---

### Post by d_xtremw on 2007-06-29
how do u set up the program to download thru a different port in each instance??

---

