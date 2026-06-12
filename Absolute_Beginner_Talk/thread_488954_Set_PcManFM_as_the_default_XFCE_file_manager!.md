---
title: "Set PcManFM as the default XFCE file manager!"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by sunexplodes on 2007-06-30
I've just started using XFCE, and as much as I appreciate Thunar, I much prefer PCManFM, so how do I set it as the default?

As well, how do I set firefox to use it as the default as well? Every time I click "open containing folder" in firefox, it opens it in Nautilus.

---

### Post by sunexplodes on 2007-06-30
anything?

---

### Post by atonello on 2007-07-06
This interests me, as well
I would like to know how to set Thunar as default file manager in firefox 
(I'm in Ubuntu 7.04 > Gnome)

Thanks :)

---

### Post by sausagepotato on 2008-01-13
sorry if i'm quite a few months late, but I was also trying to figure out how to set pcman as the default file manager, and i found this. [http://ubuntuforums.org/showthread.php?t=539182](http://ubuntuforums.org/showthread.php?t=539182)

---

### Post by emichan on 2008-06-16
I found one way to ensure that pcmanfm replaces thunar: symlink the pcmanfm binary to the thunar link and Thunar binary in /usr/bin.

In /usr/bin, you should see a symlink called thunar that links to the Thunar binary. So first, rename the thunar/Thunar link/binary files (you'll have to use sudo) - i just renamed them to thunar_ and Thunar_ respectively.

Then create new symlinks with those names that points to the pcmanfm binary

```

$ cd /usr/bin
$ sudo ln -s pcmanfm thunar
$ sudo ln -s pcmanfm Thunar

```

The only problem I've encountered is with the desktop manager. Trying to open folders from the desktop creates some odd problems. Immediately after creating my symlinks, there would be a very long pause before the folders opened in pcmanfm (only if opened directly from the graphical desktop, not if opened from the /home/user/Desktop folder). I did a restart, now speed isn't a problem, but pcmanfm opens to /home/user and I have to close that window before the correct window will open. 

If you get this funny behavior and it bugs you, you can always have pcmanfm draw the desktop for you instead of xfdesktop, but you'll lose some functionality - the click menus, and the wallpaper lists, maybe some others. 

Hope this helps! :mrgreen:

---

### Post by eeried on 2008-06-16
PcManFM can be buggy I find though I haven't tried it with Xubuntu. In Ubuntu it crashes when I want to open an image dir

---

### Post by emichan on 2008-06-16
> **eeried said:**
> In Ubuntu it crashes when I want to open an image dir

That's weird - in Xubuntu I haven't had any problems except for the weird desktop manager behavior. It's really fast, too - faster than Thunar.

---

### Post by emichan on 2008-06-17
Okay - I've worked out a lot of the bugginess! yay! :grin: It turns out that the package in the repository is pretty old, so I purged it and compiled from source.

At the moment, the svn trunk is lacking a configure script - not sure what that is about - so just grab the latest stable tarball (currently 0.4.3 i think) [http://sourceforge.net/project/showfiles.php?group_id=156956]("http://sourceforge.net/project/showfiles.php?group_id=156956") from here. Follow the build instructions here: [http://pcmanfm.sourceforge.net/build.html]("http://pcmanfm.sourceforge.net/build.html") 

If you want hal support, in addition to the packages listed on that page, make sure you get libdbus-glib-1-dev and run ./configure --enable-hal

Overall, a very easy build and it now plays much nicer with my desktop manager!

---

