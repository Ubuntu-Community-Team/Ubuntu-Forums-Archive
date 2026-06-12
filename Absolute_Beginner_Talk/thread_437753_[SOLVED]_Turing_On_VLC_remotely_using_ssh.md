---
title: "[SOLVED] Turing On VLC remotely using ssh"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by uclalinux on 2007-05-09
I have two computers in my room a server running gnome and ubuntn 7.04, and my laptop.  My ubuntu has a huge monitor attached to it, I use it as a TV. I would like to know how to turn on VLC player remotely from my laptop using ssh. This way i can lay in bed and switch what vlc is playing without getting up and changing it on the server keyboard. 

Thanks

---

### Post by fakie_flip on 2007-05-09
after you login through ssh, do this

export DISPLAY=:0

then when you open vlc, it will show up on the computer you are logged into through ssh. to play the video you want, just put its name after vlc if it is in the same directory.

vlc video_name.avi

---

### Post by uclalinux on 2007-05-09
Thank You So Much !

---

