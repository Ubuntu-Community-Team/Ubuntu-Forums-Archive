---
title: "Got 3D working(ATI) but now no desktop effects... what gives?"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by -Ghost9- on 2007-07-21
so is it not possible to have ATI acceleration ***and ***compiz desktop effects working?

---

### Post by misfitpierce on 2007-07-21
They say it is on ATI 8.39 drivers... I use 8.38 with XGL session to run compiz fusion flawlessly... No 3d accel while in XGL b/c compiz and so on are using it. So maybe with new drivers but thats about it.

---

### Post by -Ghost9- on 2007-07-21
> **misfitpierce said:**
> They say it is on ATI 8.39 drivers... I use 8.38 with XGL session to run compiz fusion flawlessly... No 3d accel while in XGL b/c compiz and so on are using it. So maybe with new drivers but thats about it.

how do i find those drivers? I followed the sticky in these forums to get the 3d driver working.

---

### Post by LuisAugusto on 2007-07-21
> **-Ghost9- said:**
> how do i find those drivers? I followed the sticky in these forums to get the 3d driver working.

You don't need those drivers, just make a XGL session like this:

```
sudo apt-get install xserver-xgl
```

```
sudo gedit /usr/local/bin/startxgl.sh
```

Copy and paste this:

```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session
```

```
sudo gedit /etc/X11/sessions/xgl.desktop
```

Copy and paste:

```
[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application
```

```
sudo chmod a+x /usr/local/bin/startxgl.sh 
```

Now, restart your computer and in GDM select XGL sessions instead of GNOME.

Hope this help, see you.

---

### Post by -Ghost9- on 2007-07-21
> **LuisAugusto said:**
> 

```
sudo gedit /etc/X11/sessions/xgl.desktop
```

Copy and paste:

```
[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application
```


when I try this part, I get an error:

Could not save the file /etc/X11/sessions/xgl.desktop.

Unexpected error: File not found


and now for some reason i have no sound.

---

### Post by -Ghost9- on 2007-07-21
ok. now that my crap is messed up, how do I revert it back so I can get my sound back?

---

### Post by Motoxrdude on 2007-07-21
> **-Ghost9- said:**
> ok. now that my crap is messed up, how do I revert it back so I can get my sound back?

That's an independant problem; wasn't caused by xgl.

---

### Post by -Ghost9- on 2007-07-21
> **Motoxrdude said:**
> That's an independant problem; wasn't caused by xgl.

ook.. then what could've caused it because up until I did what was posted in this forum, i had sound.

---

### Post by LuisAugusto on 2007-07-21
> **-Ghost9- said:**
> when I try this part, I get an error:

Could not save the file /etc/X11/sessions/xgl.desktop.

Unexpected error: File not found


and now for some reason i have no sound.

```
sudo mkdir /etc/X11/sessions
```

And keep doing the rest, btw, the sound has nothing to do whit the X server.

Hope this time really help you.

See you.

---

