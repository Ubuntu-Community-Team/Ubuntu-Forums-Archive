---
title: "640x480!!  Aaaaargh!"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by weirdlookinguy on 2007-01-15
Hey guys, I've got Ubuntu running on a modern PC, P4 2.53Ghz, 512Mb of RAM, etc...

I switched monitors from a nice 17" Philips to a (nicer and brighter, but smaller) 15" Sony CRT (Trinitron rules!).  Anyway, the screen resolution went down to 640x480 at 60Hz!  It won't let me change the resolution, in the drop down menu there are no options, so it defaults to 640x480!  Aaaargh!  Help anyone?  The computer has Integrated Intel graphics.'

Thanks, weirdlookinguy

---

### Post by kilou on 2007-01-15
I'm not sure if this solves your problem but you can try:

In the terminal type **sudo gedit /etc/X11/xorg.conf** and add your resolution in fron t of all the others in the file (scroll down, you'll see a list of resolution, just put yours before the others between brackets). Restart X by pressing Ctrl+Alt+Backspace and login.

---

### Post by Papillonrus on 2007-01-15
kilou  	would this help me with the neomagic 256av and do I have to log in as root to edit the xorg.conf:

In the terminal type sudo gedit /etc/X11/xorg.conf and add your resolution in fron t of all the others in the file (scroll down, you'll see a list of resolution, just put yours before the others between brackets). Restart X by pressing Ctrl+Alt+Backspace and login.

---

### Post by peabody on 2007-01-15
It could be that monitor doesn't work with the xserver plug and play (dpms) in which case you may have to manually specify the monitor's refresh rate manually or choose a monitor profile close to it.  I thought there was a gui tool for this, but the more I look, the more it appears there isn't one.  From a gnome terminal running "sudo dpkg-reconfigure xserver-xorg" should bring up a configuration wizard in a terminal that can help with this.  If this is wrong or if someone knows of a more user friendly way, please chime in.

---

### Post by TheOtherLinuxFreak on 2007-01-15
maby try > sudo dpkg-reconfigure xserver-xorg

then when it comes to the part where it lists all the reselutions, then press space to only slect the reselution that u want. after that press ctrl + Alt + backspace to restart the xserver. if it still does not work then do xserver again and when it comes to the part where u pick 24bit, 16bit etc... then slect 16bit or the next one down from what it is set up now.

---

### Post by weirdlookinguy on 2007-01-15
peabody's method worked great!  Thanks guys!

---

