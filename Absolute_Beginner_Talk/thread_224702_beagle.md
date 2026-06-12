---
title: "beagle"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by yellowtuesday on 2006-07-28
I've installed beagle using the *sudo apt-get install beagle* command. It's now installed how do i turn it on?

---

### Post by s_h_a_d_o_w_s on 2006-07-28
It should be in Application -> Accesories -> search if I am correct.

---

### Post by yellowtuesday on 2006-07-28
how do I get it in the top right hand corner of the screen? like in all the screen shots?

---

### Post by ape on 2006-07-28
You need to make sure that you've installed the 'deskbar-applet' package and then add the deskbar-applet to your panel.

---

### Post by dio525i on 2006-07-28
[http://beagle-project.org/Starting_Beagle_Daemon](http://beagle-project.org/Starting_Beagle_Daemon)

---

### Post by mostwanted on 2006-07-28
Run ```
beagle-search --icon
```.

Remember to set up your file-system to use extended attributes correctly:

[http://beagle-project.org/Enabling_Extended_Attributes](http://beagle-project.org/Enabling_Extended_Attributes)

dio525i is not correct, the beagle daemon is the backend, not the graphical part. If the install went well, the backend should already be running when you re-login.

ape is not correct either, the deskbar applet is just another way of accessing Beagle, but not the only or the official way.

---

