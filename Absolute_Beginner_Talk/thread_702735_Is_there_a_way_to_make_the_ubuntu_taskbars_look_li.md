---
title: "Is there a way to make the ubuntu taskbars look like they do in linux mint?"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by talvon on 2008-02-20
I much prefer the look of linux mint, basically it looks like this:

[http://img78.imageshack.us/my.php?image=mintls2.png](http://img78.imageshack.us/my.php?image=mintls2.png)

Similar to windows :P

Also, I much prefer having only 1 taskbar instead of 2.

Does anyone know if there is a way to install ubuntu and make it look like this? Its the only thing preventing me from going back to ubuntu lol (Sad I know >_<). I'd rather use ubuntu because these forums are more helpful, and I'd like to get into the nitty gritty with the command tool sometimes :)

Also, does anyone know how to get KDE to work with my volume and shortcut buttons on my keyboard? They don't do anything in KDE, but they couldn't work better in gnome. Maybe there's a way to get Kubuntu to load gnomes keyboard manager thingy?

Thanks :)

---

### Post by Cew27 on 2008-02-20
i presume you want the mint menu, i would also like this as i like the look and feel of mint but there is no 64 bit version

---

### Post by spiderbatdad on 2008-02-20
Add to your sources.list

deb [http://www.linuxmint.com/repository](http://www.linuxmint.com/repository) daryna main upstream import


then


sudo apt-get update
sudo apt-get install mintmenu

Then remove the repo.

Or follow that link and download the deb from the repo.

---

### Post by talvon on 2008-02-20
Thats exactly what I want :P

Looks like you can use this:

[http://ubuntuforums.org/showthread.php?t=621000&page=3](http://ubuntuforums.org/showthread.php?t=621000&page=3) to install it

But then again I also found out about editing and deleting panels, so hopefully I could customize the ubuntu panel to just 1 panel now that is similar looking to the mint one, that was the main reason I wanted it.

Cheers for the prompt :D

Edit: Sorry spiderbatdad, was writing this post before I saw yours.

Thanks, sounds as easy as 3.142, I'll get right on it :P

---

### Post by erginemr on 2008-02-20
The theme of Linux Mint is Murrina Green:
[http://www.gnome-look.org/content/show.php/MurrinaGreen?content=67185](http://www.gnome-look.org/content/show.php/MurrinaGreen?content=67185)

And one forum user (irielion) has repackaged this menu as iriemenu, whose Debian package you can download from:
[http://ubuntuforums.org/showthread.php?t=612163](http://ubuntuforums.org/showthread.php?t=612163)

The package installs as panel applet, which you can activate by right clicking on the top or bottom panel.

---

### Post by timbounceback on 2008-02-20
> **spiderbatdad said:**
> Add to your sources.list

deb [http://www.linuxmint.com/repository](http://www.linuxmint.com/repository) daryna main upstream import


then


sudo apt-get update
sudo apt-get install mintmenu

Then remove the repo.

Or follow that link and download the deb from the repo.
Actually, I wouldn't recommend removing the repo, because you don't get updates for mintmenu if you do this.

---

### Post by spiderbatdad on 2008-02-20
I believe the repo can conflict with updating from Ubuntu servers. Not sure. The mint menu is available as a deb package.

---

