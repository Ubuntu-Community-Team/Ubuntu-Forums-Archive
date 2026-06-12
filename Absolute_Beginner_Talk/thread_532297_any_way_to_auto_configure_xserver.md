---
title: "any way to auto configure xserver?"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by yellowband on 2007-08-22
hi

i wanted to reinstall ubuntu on my laptpo, but i lost my desktop CD, so i used my server one instead.  i've done this before on my desktop, i had to use apt-get to install gnome and xserver-xorg.

i did the same for my laptop but i'm still getting an error that wont let xserver work properly.  I know that my computer supports what is needed for xserver, as i had ubuntu on it before.  I'm just not sure how to fix my problem.

Can someobody tell me what packages i should be installing, and if there is any script that will conifgure my xserver properly?  right now, the only packages i installed are

gnome-desktop-environment
xserver-xorg

thanks for any help.

---

### Post by splintercellguy on 2007-08-22
sudo dpkg-reconfigure xserver-xorg, or sudo dpkg-reconfigure -phigh xserver-xorg if you just want the auto-detected X settings.

---

### Post by yellowband on 2007-08-22
great, thanks for the tip splintercellguy.

how do i run these scripts once i use dpkg to get them?

---

### Post by splintercellguy on 2007-08-22
You're not downloading anything, dpkg-reconfigure reconfigures the packages.

---

