---
title: "Compiz/Emerald???"
date: 2007-10-27
forum: Apple Intel Users
---

### Post by windowsesunamierda on 2007-10-27
Hello. So I installed 7.10, the fglrx drivers for my ATI and I had to install XGL in order to use the Desktop Effects.
I would like to have those nice themes that everyone is having on their computers. What do I have to do? Do I have to install Emerald theme or I already have it with the desktop effects enabled? Is the same emerald themes than compiz themes? What's the difference?
Please, tell me step by step what do I have to do to enjoy those nice themes I see on the Internet.
Thanks

I have Ubuntu 7.10 on an iMac Intel Core Duo 1.83 with an ATI X1600

---

### Post by cyberdork33 on 2007-10-27
> **windowsesunamierda said:**
> Hello. So I installed 7.10, the fglrx drivers for my ATI and I had to install XGL in order to use the Desktop Effects.
I would like to have those nice themes that everyone is having on their computers. What do I have to do? Do I have to install Emerald theme or I already have it with the desktop effects enabled? Is the same emerald themes than compiz themes? What's the difference?
Please, tell me step by step what do I have to do to enjoy those nice themes I see on the Internet.
Thanks

I have Ubuntu 7.10 on an iMac Intel Core Duo 1.83 with an ATI X1600
```
 sudo apt-get install emerald
```
Hit ALT+F2 then type:
```
emerald --replace
```

---

### Post by windowsesunamierda on 2007-10-28
Hello, I did what you told me to and everything went ok. But when I want to add new themes though the Emerald Theme Manager --> Repositories --> Fetch GPL'd Themes and Fetch non GPL'd Themes, but nothing happens.
What am I missing?

---

### Post by cyberdork33 on 2007-10-28
> **windowsesunamierda said:**
> Hello, I did what you told me to and everything went ok. But when I want to add new themes though the Emerald Theme Manager --> Repositories --> Fetch GPL'd Themes and Fetch non GPL'd Themes, but nothing happens.
What am I missing?
that has been broken... go here:
[http://www.gnome-look.org/?xcontentmode=103&PHPSESSID=c21e8e33dad50b3878fb328af20b7df7](http://www.gnome-look.org/?xcontentmode=103&PHPSESSID=c21e8e33dad50b3878fb328af20b7df7)
[http://themes.beryl-project.org/](http://themes.beryl-project.org/)

---

### Post by windowsesunamierda on 2007-10-29
OK, I downloaded a couple of themes, opened emerald and  imported with the "import" bottom. The thing is that when I select them from the list nothing happens. If I double click on them, neither. I don't get it.

---

### Post by cyberdork33 on 2007-10-29
> **windowsesunamierda said:**
> OK, I downloaded a couple of themes, opened emerald and  imported with the "import" bottom. The thing is that when I select them from the list nothing happens. If I double click on them, neither. I don't get it.
Probably won't switch immediately, the window manager has to restart. You can restart your computer, or just hit CTRL+ALT+BKSP to kill X, and it will restart again.

Be sure you are starting emerald again!

I use a little config icon like in beryl:
[http://ubuntuforums.org/showpost.php?p=3378285&postcount=12](http://ubuntuforums.org/showpost.php?p=3378285&postcount=12)

after you change a theme, just use fusion-icon to reload the window manager, and your new theme should startup.

---

### Post by hotrod6657 on 2008-01-10
If you're still looking to get the repositories working this link worked for me.  Like it says there the GPL'd themes seems to be down, but the non GPL'd themes is up.

[http://hacktivision.com/index.php?blog=2&title=how-to-install-emerald-theme-manager-in-&more=1&c=1&tb=1&pb=1]("http://hacktivision.com/index.php?blog=2&title=how-to-install-emerald-theme-manager-in-&more=1&c=1&tb=1&pb=1")

Hope that helps.

hotrod

---

