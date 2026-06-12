---
title: "Ubuntu Gimp Splash"
date: 2007-10-15
forum: Art &amp; Design
---

### Post by exploder on 2007-10-15
I put together a Gimp Splash for Gutsy. You can get it here.

[http://www.gnome-look.org/content/show.php/Ubuntu+Gimp+Splash?content=67934](http://www.gnome-look.org/content/show.php/Ubuntu+Gimp+Splash?content=67934)

---

### Post by smartalecks on 2007-10-15
can't wait till 2.4 is released and hits the repos xD ty

---

### Post by exploder on 2007-10-15
Gutsy has RC3, so I figure it will end up with the final.

---

### Post by Steveway on 2007-10-15
> To use the splash just open a terminal, type "sudo nautilus" and copy the splash to: /usr/share/gimp/2.0/images/

God beware! Never use sudo for a graphical application! Never!
The correct command should be :
gksu nautilus

---

### Post by por100pre1 on 2007-10-15
Put it on your desktop.

```
sudo mv /usr/share/gimp/2.0/images/gimp-splash.png /usr/share/gimp/2.0/images/gimp-splash.png_backup
```

```
cd Desktop
```

```
sudo mv 67934-gimp-splash.png /usr/share/gimp/2.0/images/gimp-splash.png
```

---

### Post by anonymi2 on 2007-10-15
> **Steveway said:**
> God beware! Never use sudo for a graphical application! Never!


Why?

---

### Post by bashveank on 2007-10-15
> **anonymi2 said:**
> Why?

Because sudoing a graphical program is a serious security risk.
[Can also screw up Your computer.]("http://ubuntuforums.org/showthread.php?t=181867")

---

### Post by raggari on 2007-10-16
> **bashveank said:**
> Because sudoing a graphical program is a serious security risk.
[Can also screw up Your computer.]("http://ubuntuforums.org/showthread.php?t=181867")

Why its then allowed? No normal user really see difference.

---

