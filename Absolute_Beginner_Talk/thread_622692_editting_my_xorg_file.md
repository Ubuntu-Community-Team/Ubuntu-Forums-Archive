---
title: "editting my xorg file"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by gamer4lyf3 on 2007-11-25
I have a problem with my monitor giving me a input not supported box bouncing around the screen. I found the solution but it involves editing the xorg file. How do I go about editing it correctly without ruining my xorg file? also How do I back up my xorg file? I have to add a few lines and have no idea how to go about doing this correctly. Here is the solution [http://ubuntuforums.org/archive/index.php/t-420677.html](http://ubuntuforums.org/archive/index.php/t-420677.html)

---

### Post by LaRoza on 2007-11-25
Use a live cd if the installation doesn't work.

From the live cd:

Make a copy of:

/etc/X11/xorg.conf 

That path is not the exact one, that is the path for an installed system, look on the Ubuntu partition for it, copy and save the copy in the same directory.

Now, edit the xorg.conf to the specs given.

EDIT: I noticed this problem doesn't involve the screen not working at all, use the following advice (I thought it was a no display at all issue)

---

### Post by FuturePilot on 2007-11-25
Yes, it would be a very good idea to back it up first, so do this
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_old
```
This command will make a copy of your current xorg.conf in the same directory called xorg.conf_old. So if anything happens to go wrong later, simply do this to restore your good xorg.conf
```
sudo cp /etc/X11/xorg.conf_old /etc/X11/xorg.conf
```

Now to edit it.
```
gksudo gedit /etc/X11/xorg.conf
```
This will open the file with root privileges so you can make changes. Just be careful.
After you're done, save, log out and log back in for the changes to take effect.

---

