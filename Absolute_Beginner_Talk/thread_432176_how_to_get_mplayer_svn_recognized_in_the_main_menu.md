---
title: "how to get mplayer svn recognized in the main menu?"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by ryan321 on 2007-05-03
hi i installed the mplayer svn version and it runs fine if i just type mplayer in the terminal.
However i cant add frontends like smplayer through apt-get install because it says i didnt install mplayer. I understand if i installed mplayer through apt-get install as well then frontend will work. How can I get the front end if i want to keep the svn version of mplayer?

---

### Post by shirilover on 2007-05-03
You need to pass the --enable-gui option when you run the configure script.
Then you need to download a skin from [http://www.mplayerhq.hu/design7/dload.html]("http://www.mplayerhq.hu/design7/dload.html").

Untar the archive and copy the resulting folder to ~/.mplayer/skins

The other option, if you really want to use smplayer, is to download the source code for smplayer and com pile it as well. 
I tried it and it's fairly simple; you do need the qt3 development packages though.

---

### Post by kodoku on 2007-05-03
The key is to trick apt into thinking that you installed the mplayer in the repositories.

When you './configure' and 'make' the source, you need to finish the operation with 

> sudo checkinstall

Then, you need to modify the deb details, which is done in the checkinstall process.  You need to change the program name (the svn defaults to mplayer-checkout-snapshot or something) to just 'mplayer', and change the version to the one that matches the one in the repositories (the current one is 2:1.0~rc1-0ubuntu9), or else Software Update will repeated tell you to update your installed version.

Then you install the deb, and your package manager will recognize it as the latest version of mplayer.

---

### Post by ryan321 on 2007-05-04
how do i modify the deb details??

---

