---
title: "Resolution Problems With Screen"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by stonecoldjha on 2008-03-01
hi,
my monitor shows a message with a blackout,"out of range".
to resolve it i took the following steps.

i went to the terminal and typed the following commands:
sudo cp /boot/initrd.img-`uname -r` /boot/initrd.img-`uname -r`.mybackup
sudo cp /etc/usplash.conf /etc/usplash.conf.mybackup
gksudo gedit /etc/usplash.conf

and as a result the following showed up
# Usplash configuration file
xres=1280
yres=1024
i changed it to
# Usplash configuration file
xres=1024
yres=768
then i saved the file.and then i typed
sudo dpkg-reconfigure -phigh usplash


after it successfully executed ,i rebooted but still was prompted to allow Ubuntu to run in low graphics mode.it said that my graphics card and monitor could not be detected.i even tried saving a resolution of 800*600,but it doesn't work.moreover i have downloaded the updates as i was prompted to,but still can't run desktop effects.plz help.

---

### Post by WestCoastSuccess on 2008-03-01
What's the resolution of your monitor?

I used to have the same "signal out of range" message, and as a workaround I used Ctrl+Alt+Backspace and the login screen would appear fine.

See here, too: [http://ubuntuforums.org/showthread.php?p=4434794&posted=1#post4434794](http://ubuntuforums.org/showthread.php?p=4434794&posted=1#post4434794)

Cheers.

---

