---
title: "screen resolution"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by elevation2k on 2006-10-04
Ubuntu on my Vaio laptop doesn't let me change resolution- there's no other option except 1024x768, which is annoying b/c I want it to display at 1280x800. What can I do to change this? It's running with an Intel GMA 915. I know a bunch of other people have this problem; I just found nothing conclusive on how to fix it.

Thanks in advance for any replies.

---

### Post by fritz_monroe on 2006-10-04
That's odd, on my Vaio, Ubuntu picked up the video fine and displayed 1280x800 without me having to do anything.  In preferences I can change to 1024x768, but why would I?  Good luck with this and if you come across the solution, please post it.

---

### Post by henriquemaia on 2006-10-04
Have you tried the classical:

```
sudo dpkg-reconfigure xserver-xorg
```
?

---

### Post by mysticrider92 on 2006-10-04
Ubuntu probably has detected a different graphics chipset than you have. I found this out indirectly after adding KDE on my Ubuntu install. I don't know what program to use under Gnome to change the graphics settings other than resolution, but someone else might know.

---

### Post by bodhi.zazen on 2006-10-04
Install 915resolution via synaptic or:```
aptitude install 915resolution
sudo 915resolution 50 1280 800
```

Restart X: Ctrl-Alt-Backspace or```
/etc/init.d/gdm restart
```



For more information:

[[color=blue]bodhi's resolution solution[/color]](http://ubuntuforums.org/showthread.php?p=1566609#post1566609)

---

### Post by twrock on 2006-10-05
I added 1280x1024 to my desktop by manually editing the xorg.conf file. I'm a newbie, so I don't know if that is "right", but it worked.

In the terminal I typed:

sudo gedit /etc/X11/xorg.conf

Somewhere down in the file will be a list of screen resolutions. I just added "1280x1024" at the front of each list and saved the file. (I think I had to do "Save as" over the original name, but I don't recall at the moment.)

After exiting terminal, CTRL+ALT+Backspace reloads Gnome desktop and you should be in business.

Remember, I'm new to this, and I have no idea what precautions you should be taking to avoid some kind of catastrophic failure (like maybe backing up your xorg.conf file). Someone please correct me if I am wrong about any of this.

I assume your video system is actually capable of the resolution you want to set, right?

---

### Post by bodhi.zazen on 2006-10-05
u r correct.

Backup:

Example:```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Otherwise, not bad for a noob :)

---

