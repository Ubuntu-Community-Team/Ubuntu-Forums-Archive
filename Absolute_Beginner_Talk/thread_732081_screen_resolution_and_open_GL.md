---
title: "screen resolution and open GL"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by schecterstyle101 on 2008-03-22
I have some games (tremulous and sauerbraten) that require 3d graphics.  I enabled my nvidia driver in the restricted drivers manager, but then my screen resolution drops to 800x600.  It cannot be changed using system-preferences-screen resolution.  I searched some forums and typed this in the terminal:     sudo dpkg-reconfigure xserver-xorg   it auto detected that my monitor can handle more than 800x600 and I got my 1280x1024 res back.    Now the games won't start because it can't find a matching glx visual.  I can uninstall the Nvidia driver, reinstall it, and the games will play, but my screen resolution goes back down again.

---

### Post by Sam Lars on 2008-03-22
Try installing and using the nvidia drivers, and then run
sudo nvidia-settings
Can you set your resolution there?

---

### Post by schecterstyle101 on 2008-03-23
I got a new nvidia driver and reinstalled it, which crashed Linux, and it wouldn't restart.  Then I went into recovery mode, logged in through command prompt, and used the terminal to reconfigure (autodetect)  my display settings again, and then restarted my computer, and everything works now.  I don't really know what i did. Thanks for the help.

---

### Post by Sam Lars on 2008-03-23
Reconfiguring your display probably did the trick.  Maybe I should have suggested that first. :)

---

