---
title: "easyubuntu nvidia driver runs _slowly_"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by moredhel on 2007-01-26
[Xubuntu 6.10]

Only just started using xubuntu, had been using fedora before, but it's reliability was a bit dodgy, so i guess i count as 'beginner'.

[test]

Before installing any graphics card drivers, i run supertux, when i try to make it run opengl in the options, it instantly closes
I install the nvidia drivers through easyubuntu, run supertux and turn on opengl. This time it doesn't quit, just runs at a pitiful 3 fps.

I vaguely remember getting this problem on fedora core 5, and think i installed a different set of nvidia drivers, something like xorg drivers were slow and some others werent

Is there a reason for this, and are there different sets of nvidia drivers avaliable for ubuntu (and it's derivatives), so that I could go about using a different set?

thanks in advance~

---

### Post by zerhacke on 2007-01-26
Have you edited the /etc/X11/xorg.conf file swapping the word nv with nvidia?  Once you do this logout and log back in and it should be using the accelerated driver.

---

### Post by moredhel on 2007-01-27
thanks, in the end i used a guide from the ubuntu wiki and installed the beta nvidia drivers, but thanks anyway. I will probably just do that next time :-P

---

