---
title: "Beryl XGL ATI"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Wotching on 2007-04-02
I followed this guide: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI)

But somehow I completely forgot to do everything starting with, and following, "Postinstallation".  Guess I got carried away.

Well now Ubuntu won't boot.  I thought I might be able to execute the last few lines of code through recovery mode, but since one of the things requires a graphical interface, that won't work, will it?

How can I, with hopefully minimal effort, fix it?

---

### Post by amohanty on 2007-04-03
There really nothing in there to stop you from booting. As a matter of fact it runs on top of the Metacity window manager so that if it crashes you have a desktop.

Basically you will have to undo a whole bunch of stuff, which is doable. I can possibly write you something to do that too. However, first elts figure out why you cannot boot.

When you turn on the machine, can you get to the login window?
If not are there any error messages??

AM

---

### Post by Wotching on 2007-04-03
Sorry, lemme be more specific; the problem is not that Ubuntu is not booting.  I *believe* that it is actually booting.  The issue is that maybe somehow a graphics card driver got messed up as a result of my half-assed terminal code executing.  What happens is I select Ubuntu as the OS (I dual boot with Windows), and the progress bar loads fully.  Then my screen stops receiving input, gives me a "No signal, goin' to sleep" message, and goes black.  

When I press the power button on my computer, the screen then shows the ubuntu loading screen again as it shuts down Ubuntu.  So, it would appear that everything under the scenes is going fine.  I just can't see any of it.

---

### Post by BOBSONATOR on 2007-04-03
boot into recovery mode, from grub, (pres escape while it is loading) and select recovery mode, 

then do a 

dpkg-reconfigure xserver-xorg, and select vesa.

boot back into edgy, and install fglrx like this. 

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

then install XGL & beryl like this

[http://ubuntuforums.org/showthread.php?t=291464&highlight=XGL+ATI+FGLRX](http://ubuntuforums.org/showthread.php?t=291464&highlight=XGL+ATI+FGLRX)

---

### Post by Wotching on 2007-04-03
I hope it doesn't matter that I don't have a "ATI Radeon Mobility 9000"?

---

### Post by BOBSONATOR on 2007-04-03
It doesnt, thats what i use on my laptop and it works great

---

