---
title: "Problem with Xserver (changed from ATI to Nvidia)"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by gregcha117 on 2007-01-08
I just changed my video card to an Nvidia 7600 GS after having a radeon x550, now Ubuntu refuses to start, it says Xserver error and when I scroll through it says something about Xorg.conf and ATI radeon... I had it set up to use compiz and aixgl, how can I get this working again ?

---

### Post by harmeet on 2007-01-08
please post your xorg.conf file here. In my opinion all you need to change is some settings. I am assuming you did not install nvidia driver yet. Try using "vesa" driver if that brings X back to life.

---

### Post by gregcha117 on 2007-01-08
i would post it but, i cant get to it because ubuntu wont start :P i cant get to the login screen

---

### Post by scj on 2007-01-08
Do you have a LiveCD?  If so, use it, if not, hit ctrl-alt-f1 when the login screen is supposed to come up.  (this will take you to a terminal)

---

### Post by gregcha117 on 2007-01-10
it starts fine with the livecd but i cant change anything and it still doesnt start up normally

---

### Post by gregcha117 on 2007-01-14
is there a way i can change the xorg.conf without being able to logon? i dont think i made a backup and if i did i dunno what i named it...

---

### Post by kinematic on 2007-01-14
boot up in recovery mode....this will log you in as root in a shell.
to edit your xorg.conf use this command
> nano -w /etc/X11/xorg.conf
scroll down to section "device" and change the driver to vesa.....then hit Ctrl+x so save the change and close nano.
then logout from root,log in as user and type "startx".....see if this does the trick.
you can then install the nvidia driver from the repo or the nvidia site.

---

### Post by gregcha117 on 2007-01-15
thanks so much that worked great, i tryed to do the same thing but before all id ever edited with was gedit, which xorg.conf showed up blank with when i did that under recovery mode

---

