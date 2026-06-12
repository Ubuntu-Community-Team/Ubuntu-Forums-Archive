---
title: "Install GTK Theme"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by Riyonuk on 2007-01-17
Ok, I downloaded a couple of themes, extracted them to ~/.themes and applied them from System > Prefrences > Themes yet they never look like they do on the screenshots. Mainly the tasks, on the taskbar. What am I doing wrong?

---

### Post by kerry_s on 2007-01-17
Make sure you install gtk2-engines-pixbuf, alot of themes are starting to use it but don't say it's needed.

---

### Post by Riyonuk on 2007-01-17
I installed it yet nothing changed, do I have to mess with the GTK config file?

---

### Post by ComplexNumber on 2007-01-17
try logging out then back in. it may just need to refresh the X server.

---

### Post by Riyonuk on 2007-01-17
Kinda...Im trying to get back to default gnome, but when I go to Human, it doesnt change the taskbar. Does this have something to do with murrine or switch2?

---

### Post by ComplexNumber on 2007-01-17
> **Riyonuk said:**
> Kinda...Im trying to get back to default gnome, but when I go to Human, it doesnt change the taskbar. Does this have something to do with murrine or switch2?
default gnome?? do you mean clearlooks? 
what exactly do you mean by it doesn't change the taskbar?



btw if you have the same theme in your home directory(ie .themes) as in your systemwide directory(ie /usr/share/themes), the system will use the one in your home directory.

---

### Post by Riyonuk on 2007-01-17
Well I typed in the terminal "switch2" and changed it from clearlooks to Human, and now its normal again. Do I have to do this for each theme?

---

### Post by kerry_s on 2007-01-17
I think your installing it wrong. In gnome just drag the zipped theme and drop it on the preference window it will ask if you want to install. If your just dropping it all in /.themes your only installing that one part and not the whole theme. Also you should not use another application to manage your themes, using switch2 uses a gtkrc.2.0 file which will override any other theme settings. You will need to delete that hidden /.gtkrc.2.0 file so gnome can manage the themes again.

---

### Post by ComplexNumber on 2007-01-17
> **Riyonuk said:**
> Well I typed in the terminal "switch2" and changed it from clearlooks to Human, and now its normal again. Do I have to do this for each theme?
i'm not entirely certain what the problem is. can you make a screenshot of how everything looks when you say that they don't look right? and no, you shouldn't have to do that for every theme.




> In gnome just drag the zipped theme and drop it on the preference window it will ask if you want to install. If your just dropping it all in /.themes your only installing that one part and not the whole theme.i don't recommend using gnome theme manager to install themes because it can't handle situation where there is more than one theme or file in the tarball. to see what i mean, try installing [this]("http://gnome-look.org/content/show.php?content=48681")  from gnome-look using the theme manager.
i recommend dropping the theme directly into either .theme or /usr/share/themes(for theme to be available systemwide) because thats the best way.

---

