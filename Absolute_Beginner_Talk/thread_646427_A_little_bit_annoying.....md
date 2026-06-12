---
title: "A little bit annoying...."
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by kona0197 on 2007-12-21
OK so I changed my login screen. The default "brown" one is not one I prefer. 

The annoying part is that while booting *after* entering a password the system shows a whole brown screen shortly before GNOME takes over.

Can I change that?

---

### Post by JillSwift on 2007-12-21
Yep.

1) Edit [COLOR=DarkRed]/etc/gdm/PreSession/Default[/COLOR] as a super-user:```
gksudo gedit /etc/gdm/PreSession/Default
```

2) Find the line that says **BACKCOLOR="#DAB082"** and change it to the HEX color of your choice. For instance, black is: BACKCOLOR="#000000".

3) Save the file and reboot.

---

### Post by daou on 2007-12-21
Might be easier with gdmsetup

```
sudo gdmsetup
```

Then go to the Local tab, and you will find a color chooser for the background color.

---

### Post by philinux on 2007-12-21
There's a much simpler way.

System>Admin>LoginWindow

click Local Tab 

Look half way down is background colour. Change it to your choice.

---

### Post by kona0197 on 2007-12-22
> **daou said:**
> Might be easier with gdmsetup

```
sudo gdmsetup
```

Then go to the Local tab, and you will find a color chooser for the background color.

Tried that - still shows the brown color. I also tried the LoginWindow and that didn't help...

---

