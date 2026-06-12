---
title: "Adding Icons"
date: 2006-05-11
forum: Absolute Beginner Talk
---

### Post by CybaCowboy on 2006-05-11
Okay,

I've worked out on my own that some (most?) image formats can be used for icons in the menu, but how do I add images I've downloaded for the sole-purpose of icons use to the same directory where all my other icons are stored (usr/share/pixmaps)?

I tried to cut & paste the image there, but that nor saving the file directly would work!

---

### Post by Sutekh on 2006-05-11
That's because all folders outside of your home folder /home/<username> are not able to be written to as a normal user.

As the root user you can write to these folders, using **sudo** to achieve it.

You can copy the icons using the terminal command, cp
```
sudo cp /<path of icons> /usr/share/pixmaps
```

If you want to use Nautilus (the file browser) to click and drag, then you need to start it as root using
```
gksudo nautilus
```

---

### Post by tenn on 2006-05-11
Sutekh beat me to it :)

I put my icons in 
/usr/share/icons 
and that works fine, you need root permission to right to those directories you could use the command line or just do [gksudo nautilus] in the terminal to do cut and paste with nautilus.

---

