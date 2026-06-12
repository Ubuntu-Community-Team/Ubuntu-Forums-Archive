---
title: "Installing Murrine"
date: 2007-03-26
forum: Art &amp; Design
---

### Post by gingin on 2007-03-26
How to get Murrine theme running?

I have downloaded and installed New Murrine Configurator.
Downloaded theme self.

Theme is in  mine : /home/gin/themes
The problem is as Murrine Configurator cant find that theme.

Im just would like to ask how correctly to reconfigurate that murrine configurator make to see  that theme?

Do i have to install in to the /usr/share/themes ?
And how to do that?

Thank guys for help.

---

### Post by ComplexNumber on 2007-03-26
what exactly is the name of the murrina theme?

---

### Post by gingin on 2007-03-26
I would like to install same thing called MurrinaCobalt.

---

### Post by ComplexNumber on 2007-03-26
i don't know why it doesn't show up in murrina configurator. i already have it on my system, but to enable me to replicate why you can't see it, i downloaded it fresh from gnome-look, then placed in my ~/.themes directory. i then ran murrina configurator, and it shows up perfectly.

btw do you create the directory "themes" manually in your home directory? note that there is a dot before the directory (ie **.**themes)

---

### Post by gingin on 2007-03-26
Yes. i did crated directory manually,but it have no **dot** befor directory because Ubuntu has refused to rename with a dot. 
It says as such directory exist and I should rename it. But such name doesnt exist in mine home directory anless is hiden.

But I will tray do do again:
freshly download theme from the gnome -look and create new directory with a dot.
Actually I have followed instructions in a [http://ubuntuforums.org/showthread.php?t=239378&highlight=murrina](http://ubuntuforums.org/showthread.php?t=239378&highlight=murrina)

---

### Post by ComplexNumber on 2007-03-26
> i did crated directory manually,but it have no **dot** befor directory because Ubuntu has refused to rename with a dot.thats why it doesn't show up. the directory .themes (ie dot themes) is a standard directory that murrina configurator looks for.
delete the one that you manually created and use .themes instead.

**NOTE: **to show hidden files, select 'Edit' in nautilus' menu, then 'preferences'. then tick 'show hidden files and backup files'. if you then find that there is no .themes directory, then you can create it. but it MUST be called ".themes".


you will then find that murrina-cobalt will show up in murrina-configurator.

---

### Post by gingin on 2007-03-26
It was another problem. 
Same how folders was hidden and this is why I could not create directory with a **dot** .
I have unhidden those hidden folders and everything was just perfect. Know murrinas configurator can see theme.

Thank you very much for helping me out

---

