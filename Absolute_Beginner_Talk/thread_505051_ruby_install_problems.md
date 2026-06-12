---
title: "ruby install problems"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by JewelledDragon13 on 2007-07-19
trying to install the ruby-gnome2-all package.  I've got it extracted (in /usr/lib).  The readme says to run ruby extconf.rb, but when I do so, I get this error:

extconf.rb:9:in `require': no such file to load -- mkmf (LoadError)
        from extconf.rb:9

What's wrong?

---

### Post by tbroderick on 2007-07-21
I'd suggest installing ruby-gnome2 from the repo. It's the same as ruby-gnome2-all. Ubuntu/Debian just has a slightly different naming scheme.

---

