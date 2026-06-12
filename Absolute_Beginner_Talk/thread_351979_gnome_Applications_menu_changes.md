---
title: "gnome Applications menu changes?"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by kpham.p on 2007-02-02
Hello guys,

Is there a way that I can change the look of Gnome's Applications menu? I'd like to make the icon and text smaller then the default setting, I wanted to make the applications menu small like KDE's menu.    the reason is because when I installed too much stuff, the menu start to be longer than my screen size.  I wonder if anyone out there know how to change it to a smaller size.

many thanks,
Kpham.p

---

### Post by randomnumber on 2007-02-02
System->Preferences->Font 

Application Font

---

### Post by kpham.p on 2007-02-04
Thank you randomnumber for your reply.  However, it is still big because of the icon next to the application font.  I wonder if I can shrink the icon to make the menu a little shorter.

thanks,
Kpham

---

### Post by randomnumber on 2007-02-04
i don't know how to do that. perhaps you can change the size of the icons themself. that would be a lot of work and it might not work

---

### Post by kpham.p on 2007-02-04
I see, Thanks.  I guess I can just remove the icon from the menu.

thanks,
kpham

---

### Post by Shinoda on 2007-02-27
If you mean the icons in the menu that pops up upon clicking Applications, open [FONT=Courier New]~/.themes/<current theme's name>/gtk-2.0/gtkrc[/FONT] in a text editor (assuming of course it's a GTK 2 theme), find a line looking like
```
#gtk-icon-sizes = "panel-menu=24,24:panel=24,24:gtk-button=16,16:gtk-large-toolbar=24,24"
```and change it to something like
```
gtk-icon-sizes = "panel-menu=16,16:panel=16,16:gtk-button=16,16:gtk-large-toolbar=24,24"
```(you'll probably need to [FONT=Courier New]killall gnome-panel[/FONT] afterwards to see the changes).
In case anyone knows whether there's a way to globally effect this, i.e., that doesn't require changing every theme's [FONT=Courier New]gtkrc[/FONT] file, please feel free to let us know.

---

