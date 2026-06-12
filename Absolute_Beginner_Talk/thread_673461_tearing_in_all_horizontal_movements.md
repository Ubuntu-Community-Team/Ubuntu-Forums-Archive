---
title: "tearing in all horizontal movements"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by hashimmuqtadir on 2008-01-20
I installed ubuntu and everything works fine, apart from the fact that there is tearing if I drag windows horizontally, play videos, etc.

I use an nvidia geforce fx5200, driver 169.07 installed using envy.
I have tried using sync to vblank in nvidia-settings, and tried to correct the refresh rate which is shown 50Hz instead of 60, but doesn't work. Actually I ended up making the refresh rate show 69Hz.
Anyway, what else can I do about it?

---

### Post by GGLucas on 2008-01-20
Are you using compiz ? If so, is Sync to VBlank enabled in your CompizConfig ? It's under General => "Display settings" tab. Do you have AiGLX or XGL enabled ?
I had this myself a while back, I tried a lot of things and somewhere in enabling Sync to VBlank in compiz or adding a line for AiGLX in my xorg.conf, it got fixed. (It might also help to use "Fast" under Texture Filter in Compiz, there will be more jaggies and it will look a bit worse, but it does make it a lot faster.)

---

### Post by hashimmuqtadir on 2008-01-21
THANKS!!! That solved it. Now I'm wishing I had posted earlier instead of googling for hours.

---

### Post by hashimmuqtadir on 2008-01-21
Actually the tearing has not gone altogether, it is still noticeable when I play videos in MPlayer or totem or VLC, but even then it has been greatly reduced.

---

### Post by GGLucas on 2008-01-21
For mplayer, there's two things you can try, the first one is easy, the default GUI for mplayer is bad, it's buggy and there are very little features, if you download smplayer, you'll have access to a lot more options to toy around with to try and make mplayer work better, you can get the deb/tarball from:
[http://smplayer.sourceforge.net/downloads.php?tr_lang=e]("http://smplayer.sourceforge.net/downloads.php?tr_lang=e"), you should particularly note the "video" tab in the general options in options => preferences, tweaking with the direct rendering or postprocessing might give you a good result.

Secondly, you can try compiling the latest mplayer svn version from source, although you should be prepared to reinstall or recompile it if there's a bug in the current svn version:

First, checkout the latest source from mplayer.
```
svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer
```

Get build dependencies:
```
sudo apt-get build-dep mplayer
```

Move to the directory and compile it:
```
cd mplayer
./configure
make
sudo make install
```

The "make" step might take a whiiile (it takes about 10-20 minutes here). After you're done, restart smplayer/gmplayer (default GUI)/mplayer (no GUI), if it bugs up and mplayer stops working, reinstall it by doing:
 ```
sudo apt-get install --reinstall mplayer
```

---

### Post by hashimmuqtadir on 2008-01-22
I had an mplayer release installed with the default gui (I think I installed it from the repos) , but I installed another version using subversion (without uninstalling the older one) and now if I type mplayer -vo help in the terminal I do not get Xv as an available output driver. I am using smplayer as a frontend now and... What has gone wrong? I used xv before, and it's still usable in VLC. And, as a sidenote, xv in VLC seems to produce more tearing than gl2 in mplayer. For some reason VLC is unable to play using OpenGL.

---

