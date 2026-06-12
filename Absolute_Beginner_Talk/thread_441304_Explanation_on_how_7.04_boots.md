---
title: "Explanation on how 7.04 boots"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by winksaville on 2007-05-12
Hello,

This morning ubuntu only boots to the command line and not into Gnome.
I've done some searching of the forums and found that 7.04 uses
upstart to boot and event.d is important.

Could someone direct me to an explanation of how 7.04 actually
boots and maybe some clues on how I might determine why Gnome
isn't running.

Thanks,

Wink Saville

---

### Post by Bachstelze on 2007-05-12
"how Linux boots " is a very, very, *very* broad topic ! Since your concern is about X not strating, do you see any error message about it ?

---

### Post by trent dillman on 2007-05-12
...

---

### Post by jfinkels on 2007-05-12
Try startx; you can also try:```
sudo /etc/init.d/gdm start
```to see if the GNOME Display Manager (the login screen) will start up.

---

### Post by [S|G] on 2007-05-12
The most likely cause is that your X configuration is somehow botched. If you have installed official video card drivers, a kernel upgrade might have caused that. You can try reinstalling your video drivers or you can try this:
```
sudo dpkg-reconfigure xerver-xorg
```
Then try to boot again.

---

### Post by winksaville on 2007-05-12
I can log in and yes "startx" boots into gnome, so thats a good start:)

What can I look at to determine why it isn't automatically booting to Gnome?

Tx,

Wink Saville

---

### Post by Bachstelze on 2007-05-12
```
sudo /etc/init.d/gdm start
```

Does that work ? (From the command-line)

---

### Post by winksaville on 2007-05-12
Is it narrowed down if I ask just how 7.04 boots?
Is there any links you can point me to that give an explanation?

Wink Saville

---

### Post by winksaville on 2007-05-12
No, "sudo /etc/init.d/gdm start" does nothing, (but startx does work).

Wink Saville

---

### Post by [S|G] on 2007-05-12
You can try reinstalling gdm:
```
sudo apt-get install --reinstall gdm
```

---

### Post by jiminycricket on 2007-05-12
have you tried sudo killall gdm first?

---

### Post by winksaville on 2007-05-12
Re-installing gdm did the tirck, thanks!!!!!

What apparently happened was last time I had booted I had installed alsa-tools and alsa-sources
but then decided to uninstall and did a "complete removal". Well apparently gdm was
part of it and it looks like it got uninstalled too.

I discovered this because after "startx" I used synaptic to look at gdm and saw that  it wasn't
installed. I "marked" and "applied" and when applying it said it need alsa-utils. After installing
and then rebooting, Gnome is back.

Sooooooo, it appears my "complete removal" of alsa was probably the problem.

Thanks everyone,

Wink Saville

---

### Post by jiminycricket on 2007-05-12
Hmm do you have ubuntu-desktop installed?  [http://packages.ubuntulinux.org/feisty/metapackages/ubuntu-desktop](http://packages.ubuntulinux.org/feisty/metapackages/ubuntu-desktop)

gdm is a dependancy of it, so i might help if any other odd issues crop up.

---

