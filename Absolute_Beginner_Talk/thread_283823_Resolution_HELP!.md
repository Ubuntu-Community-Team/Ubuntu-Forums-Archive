---
title: "Resolution: HELP!"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by PfD on 2006-10-24
Please help!
I wanted to set up my screen resolution to be higher than 1024x768 and followed this:
sudo dpkg-reconfigure xserver-xorg
mentioned in other threads regarding the same topic.

But after I reboot, the only resolution I can choose is 640x480!
What have I done wrong?

---

### Post by bigken on 2006-10-24
when you run the dpkg-reconfigure xserver-xorg did use the space bar to select your required sizes ;)

---

### Post by TitusDalwards on 2006-10-24
by manually you can change /etc/X11/xorg.conf file. 

SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
in this section you can change the resolution type instead of 1024x768

---

### Post by PfD on 2006-10-24
Yes!
But if i haven't chosen them, then I would have the old 1024x768.
Now it's terrible 640x480!

---

### Post by Chake99 on 2006-10-24
I spose you are new to linux and you're running gnome.

Go to applications accessories terminal

type sudo gedit /etc/x11/xorg.conf (I think)

you should get a config file, whenever it lists screen resolutions add 1024x768 to the front of the lists in the same format as the other res'.

restart the computer (or possible ctr-alt-del-backspace but that could backfire)

go to system preferences screen resolution.

---

### Post by bigken on 2006-10-24
which video device you selecting or is being selected for you ?

---

### Post by PfD on 2006-10-24
> **Chake99 said:**
> I spose you are new to linux and you're running gnome.

Go to applications accessories terminal

type sudo gedit /etc/x11/xorg.conf (I think)

you should get a config file, whenever it lists screen resolutions add 1024x768 to the front of the lists in the same format as the other res'.

restart the computer (or possible ctr-alt-del-backspace but that could backfire)

go to system preferences screen resolution.

Yes, I'm brand new!
In fact, I'm doing this, and 1024x768 is listed everywhere in the config file. :-(

---

