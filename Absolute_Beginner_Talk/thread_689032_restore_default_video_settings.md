---
title: "restore default video settings"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by tone33 on 2008-02-06
So I hosed my video somehow when setting Twinview options in the nvidia gui tool - how can i restore to defaults?  I came across this and executed it in a previous install (earlier today)

```

sudo dpkg-reconfigure xserver-xorg

```

and it took me through the config wizard for alll my periphereals, but i remember some strange "cannot start Hal!" error after doing so..

---

### Post by tone33 on 2008-02-06
ok so the reason i want to do this is because i no longer see the applications and system menus on my taskbar.  This is because they are on the left monitor - which is all black - and the right monitor has the ubuntu desktop.  The monitor is ok - and it actually was displaying the desktop on that monitor until my last reboot when I changed some settings in the NVidia Twinview dialog.  any ideas?

---

### Post by VoyeurOne on 2008-02-06
it might not be a lot of help if you don't see your screen,  but after many headaches setting up my video I finally settled on a package called  Envy , if you have an ATI or NVidea card it's a lifesaver as it also works from the command line and resets your video so you can at least boot in to the graphical interface.   I had to rebuild my computer last week due to HD failure first thing I reloaded was Ubuntu second was Envy :)

---

### Post by tone33 on 2008-02-06
ok thanks I'll look into it.

---

