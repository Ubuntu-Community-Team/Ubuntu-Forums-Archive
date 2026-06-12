---
title: "Help with 8800GT"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by danbrownlow on 2008-02-28
Hey there, I'm having some bigg problems with the 8800GT drivers. I've installed them as this post has shown me..[http://ubuntuforums.org/showthread.php?t=684424](http://ubuntuforums.org/showthread.php?t=684424) and now my computer has reverted to 800x600 and I cant' seem to get xserver to come back on. When I do I'm told I need to remove /tmp/.XO-lock or something like that.
Anyone able to lend a hand?

---

### Post by dstew on 2008-02-28
Boot into recovery mode. Log in. On the command line enter ```
sudo dpkg-reconfigure xserver-xorg
```If the nvidia driver was installed, you will have the choice to use that driver. If it is not there, use whatever is designated, or just use vesa for now. It can always be changed later. Once you get the desktop back, you can try to install the driver again. After you install, maybe run dpkg-reconfigure xserver-xorg again.

---

