---
title: "Metacity/GTK Themes"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by jporter91 on 2006-11-27
First of all, are do metacity and gtk themes work the same way in ubuntu with the gnome theme manager? i downloaded several gtk themes from gnome-look (most of which worked, some were "in the wrong format"). they sometimes don't look as good as they do in the screenshots though... and when i install a metacity theme, the only thing the changes is the window border. the theme i like best is "smoked glass" from gnome-look. the applications in the screenshot are more graphical than mine though. for example, with nautilus, firefox, the toolbars at the top, buttons, and controls are detailed with a blue gradient in the screenshot ( [http://www.gnome-look.org/content/pre1/27141-1.jpg](http://www.gnome-look.org/content/pre1/27141-1.jpg) ) , when i just have a solid colour for the toolbars and controls. Can someone tell me if there's a differnce between metacity and GTK or if there's something im not knowing? thanks.

---

### Post by 23meg on 2006-11-27
Metacity is your window manager, and Metacity themes only modify your window borders. GTK is GNOME's widget toolkit, thus GTK themes affect all the widgets your windows are composed of.> the applications in the screenshot are more graphical than mine though. for example, with nautilus, firefox, the toolbars at the top, buttons, and controls are detailed with a blue gradient in the screenshot ( [http://www.gnome-look.org/content/pre1/27141-1.jpg](http://www.gnome-look.org/content/pre1/27141-1.jpg) )With some GTK themes you may need to install a theme engine that doesn't come installed with Ubuntu, that may be the reason.

---

### Post by jporter91 on 2006-11-27
ok thanks:) so from what i gather, gnome theme-manager uses metacity to manage ..window borders... and GTK to change the way widgets and toolbars and buttons and stuff looks... you said metacity is my window manager... but im assuming i have GTK too? im still not understanding this completely... this theme btw doesn't require an extra theme engine i don't think... i spose ill just forget about it. btw ... dude... that was a fast response:) ty

---

### Post by 23meg on 2006-11-27
[QUOTE=jporter91]gnome theme-manager uses metacity to manage ..window borders... and GTK to change the way widgets and toolbars and buttons and stuff looks...[/QUOTE]Not exactly; gnome-theme-manager is what you use to decide which themes Metacity and GTK will use. [Metacity]("http://en.wikipedia.org/wiki/Metacity") is a program that's running by default in the GNOME environment; it manages / lets you manage windows. [GTK]("http://en.wikipedia.org/wiki/GTK") is the widget toolkit used by GNOME; it's what the buttons, scrollbars, radio boxes etc. that you see everywhere constitute. You have both installed and running in GNOME, and both are themeable, but separately.

See [this thread]("http://www.ubuntuforums.org/showthread.php?t=87276") for more information.

---

