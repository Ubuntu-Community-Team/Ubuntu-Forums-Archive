---
title: "How do I fix"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by HdK on 2006-09-02
When I boot up in KDE I get this Compistion Manager Error

Composite extension not found
You must use XOrg &#8805; 6.8 for translucency and shadows to work.
Additionally, you need to add a new section to your X config file:
Section "Extensions"
Option "Composite" "Enable"
EndSection

How do i fix it please?

---

### Post by croak77 on 2006-09-02
Do you add;
Section "Extensions"
Option "Composite" "Enable"
EndSection

To your /etc/X11/xorg.conf.

---

### Post by HdK on 2006-09-02
How exactly do I go about doing that , i don't want to screw it up more than it already is

---

### Post by croak77 on 2006-09-02
I don't think it matters where you put it. Just put it at the end of the file.

```
sudo nano -w /etc/X11/xorg.conf
```

Add,

```
Section "Extensions"
   Option "Composite" "Enable"
EndSection
```

This is assuming you have a graphics card that can handle it. If not open kcontrol and turn off translucency and shadows. You don't need it. It's just eye candy.

---

