---
title: "fluxbox + gnome-panel: inviting instability?"
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by takayuki on 2006-03-20
hi everyone,

i just got fluxbox going and love it.  i also have the gnome panel running at the same time.

per the excellent fluxbox wiki: [https://wiki.ubuntu.com/Fluxbox]("https://wiki.ubuntu.com/Fluxbox")
i've got the gnome daemon running (code snippet below) so everything seems okay...

#enable use of nautilus and gnome panels
GSDPID=`pidof gnome-settings-daemon`
if [  "x$GSDPID" == "x" ]; then
gnome-settings-daemon &
fi

gnome-panel &


i love fluxbox, but i can't pull myself away from the panel (i'm a part-time mac user--my apologies), and need a stable system to get work done.

am i worrying for nothing? 

thanks,

takayuki

---

### Post by Sef on 2006-03-20
If you followed the directions, you shouldn't have any problems with stability.

---

### Post by takayuki on 2006-03-20
thanks for the input Sef.  it's all new territory so i'm erring on the side of caution.  

i installed ubuntu two weeks ago on an old pc and, oh my, it's about to replace my beloved mac.  :)

takayuki

---

