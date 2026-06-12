---
title: "XGL and aMSN problem"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by djcawthorne on 2006-09-25
having just installed XGL on an nVidia system it appears aMSN now does not want to work.

any advice would be a great help

---

### Post by djcawthorne on 2006-09-25
> Q: When I try running aMSN, I get an error "unknown color Black". How can I fix it ?
A: This problem is not coming from aMSN, it's an Xorg faulty installation. You probably have a bad Xorg configuration for the file rgb.txt (especially with some versions of Xgl).

If you are using xgl, you most probably have the file rgb.txt in /etc/X11 . Xgl in Ubuntu Dapper is usually misconfigured and looks for the file in /usr/share/X11 . Make a symlink to it in /usr/share/X11 and restart your X server.  ive done a bit of digging and have come up with this....i have no idea what to do with it!

any help much appriciated!

---

