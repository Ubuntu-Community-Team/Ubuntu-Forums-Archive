---
title: "Cant install programs"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by systemintheglitch on 2006-02-20
I used the advanced version of the add programs screen and noticed there were more options of programs to install.. So i installed something called geta, which wans't  in the simple version.. But after i clicked "ok" or whatever, the programs werent installed.. I cant get to them through the programs menu with the ubuntu icon!! It seems nothing i install with the advanced version takes effect.

---

### Post by Nequeo on 2006-02-20
[QUOTE=systemintheglitch]I used the advanced version of the add programs screen and noticed there were more options of programs to install.. So i installed something called geta, which wans't  in the simple version.. But after i clicked "ok" or whatever, the programs werent installed.. I cant get to them through the programs menu with the ubuntu icon!! It seems nothing i install with the advanced version takes effect.[/QUOTE]

When you're using the 'advanced' mode (which you can also access through System--->Administration--->Synaptic Package Manager), you need to right click on the program you want to install and select 'Mark for installation'. Then you can press 'okay' and it will go through and install them.

Forgive me if you've done this already - but I'm taking you at face value when you say the program wasn't installed. If you've already done the steps above then the program is installed, it just doesn't have a menu entry. If that's the case, let us know and we'll show you how to add it in yourself.

Cheers,

---

### Post by Qrk on 2006-02-20
I'd recommend installing the "menu" package. It will display a menu labled "debian" under Applications, which lists most (all?) of the apps you have on your system.

---

### Post by systemintheglitch on 2006-02-20
K.. then it just doesnt have a menu entry.. how to i get it to have one.. Please speek as if i am retarded, because i am when it comes to linux.

---

### Post by Madpilot on 2006-02-20
Right-click on the Applications menu and chose "Edit Menus".

Find the sub-menu you want to add your new app to, and hit the "New Entry" button.

Give it a name, add a comment if you want (those appear as the popup tooltips when you hover over the menu item). Pick an icon if you want.

For the "Command" field, you'll usually just put the name of the application - the same name the package had in Synaptic.

If that doesn't work, post the name of the package here and someone can help you find out the command to run it.

EDIT to add: you can also just use the Terminal/command-line to launch apps that don't have menu entries. **Applications menu --> Accessories --> Terminal** and just type the name of the app, that'll usually launch it.

---

### Post by systemintheglitch on 2006-02-21
Worked Great! Thank you.

---

### Post by carlosqueso on 2006-02-21
[QUOTE=Qrk]I'd recommend installing the "menu" package. It will display a menu labled "debian" under Applications, which lists most (all?) of the apps you have on your system.[/QUOTE]


This is a great idea....I have it on mine and I'd reccomend it for you too.

---

### Post by systemintheglitch on 2006-02-21
How do i get it? Step by step?

---

### Post by Madpilot on 2006-02-21
[QUOTE=Qrk]I'd recommend installing the "menu" package. It will display a menu labled "debian" under Applications, which lists most (all?) of the apps you have on your system.[/QUOTE]

I tried using that "Debian" menu, but the trouble is that it seems to list everything that's already got a seperate menu entry, as well as a lot of other otherwise unlisted stuff - makes it hard to wade through.

These days I just add my own menu entries with Edit Menus, and sometimes file a bug against the package, so that a proper .desktop entry gets included in the next update.

---

### Post by carlosqueso on 2006-02-21
[QUOTE=systemintheglitch]How do i get it? Step by step?[/QUOTE]


Just fire up a terminal and type ```
sudo apt-get menu
```  As the above poster pointed out, some stuff will be automaticly added to the main menu and the Debian menu both, but you know that nearly everything will be added to the Debian menu.....it's all up to you.

---

