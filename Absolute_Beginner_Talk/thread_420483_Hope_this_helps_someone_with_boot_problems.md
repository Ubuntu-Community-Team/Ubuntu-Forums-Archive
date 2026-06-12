---
title: "Hope this helps someone with boot problems"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Drifter on 2007-04-23
I did a fresh install everything worked perfectly. Then a message appeared saying something about nvidia drivers and if you play games you wil need this. I installed the nvidia drivers and then I could not boot. I went to repair screen on boot and typed e on the drive listed. I then made it to command line that listed my desktop. I typed sudo dpkg-reconfig -phigh xserver-xorg. After that I typed starx I was able to get back up and running however I was not logged in right, so I went to addremove programs and uninstalled the nividia driver and all is well. I don't know how I did this or if I remember it correctly but anyway it works. Hope this helps someone.

---

