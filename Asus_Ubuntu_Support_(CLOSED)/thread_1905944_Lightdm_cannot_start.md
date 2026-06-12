---
title: "Lightdm cannot start"
date: 2012-01-08
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Euboon2 on 2012-01-08
After installing ubuntu on my asus transformer tablet with lightdm + onboard (keyboard) for logging in as normal user, the tablet boot up and could not start lightdm.

As I do not have the accompanying keyboard for the tablet, typing startx is not an option unless lightdm can be started and allows onboard to appear in the screen.

On the other hand, if I ssh into the tablet, I can log in as root user using startx. Normal user log in gives the error msg "X: user not authorized to run the X server, aborting."

I believe this has to do with lightdm's permission setting or configuration. I am trying to avoid installing gnome or kde, since this tablet's processor is rather slow and there is no hardware acceleration. Installing gnome-desktop environment should solve the problem, but they pull in lots of packages that take up a lot of space on the memory card.

dpkg-reconfigure or re-installing lightdm doesn't help.

Other display managers such as SLiM and GDM work fine, but they don't support screen keyboard. Any help is appreciated.

---

### Post by Euboon2 on 2012-01-08
Just realized lightdm has a missing dependency, which "apt-get autoremove" erroneously removes. I installed gdm and see what packages it pulls along. Then removed them and install separately each one to identify the required package/s.

---

