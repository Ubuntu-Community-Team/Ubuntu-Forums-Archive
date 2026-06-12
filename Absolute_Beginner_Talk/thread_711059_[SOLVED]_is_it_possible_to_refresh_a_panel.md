---
title: "[SOLVED] is it possible to refresh a panel?"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by cpu_medic on 2008-02-29
is it possible to refresh a panel? and if so .. how

---

### Post by kpkeerthi on 2008-02-29
killall gnome-panel

* It would close and launch back again with that command

---

### Post by cpu_medic on 2008-02-29
interesting, it did refresh, but my buttons still dont work. wtf?

---

### Post by jan quark on 2008-02-29
are you running compiz? what buttons do you mean?

---

### Post by cpu_medic on 2008-02-29
i am running compiz, but the buttons im talking about is are the desktop switcher, terminal, bluetooth, and sound, mini icons on the panel. they dont work even after a reboot, and a " killall gnome-panel "

---

### Post by kpkeerthi on 2008-02-29
I think you removed notification area from the panel.

Right-click on the panel -> Add to Panel -> Choose 'notification area'

---

### Post by cpu_medic on 2008-02-29
ok um i did that and killall gnome-panel and it still doesnt work :(

---

### Post by kpkeerthi on 2008-02-29
How about a reboot?

---

### Post by cpu_medic on 2008-02-29
ok hold on

---

### Post by cpu_medic on 2008-02-29
Ok its fixed now, thank you guys

---

### Post by adityakavoor on 2008-02-29
Hit Alt+F2 and type in gnome-terminal
now type in the following to the terminal

```


gnome-session-remove gnome-panel
gconftool-2 --recursive-unset /apps/panel
gnome-panel &


```

---

