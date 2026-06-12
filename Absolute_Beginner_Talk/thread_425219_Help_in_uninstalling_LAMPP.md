---
title: "Help in uninstalling LAMPP"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by Danilo Leon on 2007-04-27
I installed LAMPP and everything was ok until I forgot my password to run LAMPP. Now I want to uninstall it and start from a fresh install but i keep typing ```
rm -rf/opt/lampp
``` but nothing happens.  I tried ```
sudo rm -rf/opt/lampp
``` and still nothing.  I keep getting this message :rm: invalid option -- /
Try `rm --help' for more information.

Please help thanks.

---

### Post by compmodder26 on 2007-04-27
there should be a space between -rf and /opt.  So:

rm -rf /opt/lampp

---

