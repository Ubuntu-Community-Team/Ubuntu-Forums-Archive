---
title: "Installing Themes"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by VoiceOvGod on 2008-02-25
It's likely I am doing something wrong, but, I figured I would check anyway.

Installing themes on Gutsy.

No compiz/beryl installed.

Using basic effects.

What do I need to do to install a theme I got from gnome-look?

---

### Post by jken146 on 2008-02-25
Go to System -> Preferences -> Appearance and drag and drop the theme package into that window.

---

### Post by Anduu on 2008-02-26
If drag and drop gives you an error don't panic...theme makers don't always package their themes properly.

Manually extract the theme and copy the themes main folder to /home/<username>/.themes or if it is an icon theme move to /home/<username>/.icons

---

### Post by 3rdalbum on 2008-02-26
Note that you drop the .tar.gz onto the window - you don't uncompress the file first.

---

### Post by CREEPING DEATH on 2008-02-26
> **jken146 said:**
> Go to System -> Preferences -> Appearance and drag and drop the theme package into that window.

That's it?  Wow this is almost too easy!

CD

---

### Post by ADBD on 2008-03-10
> **Anduu said:**
> If drag and drop gives you an error don't panic...theme makers don't always package their themes properly.

Manually extract the theme and copy the themes main folder to /home/<username>/.themes or if it is an icon theme move to /home/<username>/.icons

I get an error drag and dropping so I tried this. I put the folder where the themes files are to /home/<username>/.themes but nothing happened. it's not showing in System -> Preferences -> Appearance. Also installing it from the installa button in appeareance window doesn't work

EDIT: oh sorry it was a login screen theme not a theme. how do i install those then?
EDIT: got it

---

### Post by sayakb on 2008-03-10
> **ADBD said:**
> I get an error drag and dropping so I tried this. I put the folder where the themes files are to /home/<username>/.themes but nothing happened. it's not showing in System -> Preferences -> Appearance. Also installing it from the installa button in appeareance window doesn't work

First of all make sure its a GTK theme (download one that says it is).
If none of the above works, just extract the archive file and copy the folder to /usr/share/themes folder while logged in as root. To open Nautilus as root:

```
sudo nautilus
```

---

### Post by aysiu on 2008-03-10
> **LinuxIsInnovation said:**
> First of all make sure its a GTK theme (download one that says it is).
If none of the above works, just extract the archive file and copy the folder to /usr/share/themes folder while logged in as root. To open Nautilus as root:

```
sudo nautilus
```
It should be ```
gksudo nautilus
```

---

### Post by sayakb on 2008-03-10
> **aysiu said:**
> It should be ```
gksudo nautilus
```

Using sudo works fine as well. Any prominent advantages of gksudo over sudo?

---

### Post by aysiu on 2008-03-10
> **LinuxIsInnovation said:**
> Using sudo works fine as well. Any prominent advantages of gksudo over sudo?
Yes, it's a good habit to get into for graphical applications. Read this:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by stchman on 2008-03-10
> **VoiceOvGod said:**
> It's likely I am doing something wrong, but, I figured I would check anyway.

Installing themes on Gutsy.

No compiz/beryl installed.

Using basic effects.

What do I need to do to install a theme I got from gnome-look?

Installing themes are somewhat non-intuitive.  You have to drag and drop the compressed archive i.e. .tar.gz instead of unpacking it.

Also as the 2nd poster said the packages are sometimes not properly packed.  They will put archives within archives sometimes.  Gnome-look.org is a great place to get themes.  I have some themes on ym site as well.

[http://www.stchman.com/themes.html](http://www.stchman.com/themes.html)

If you want an OS X look then go to [http://sourceforge.net/projects/mac4lin](http://sourceforge.net/projects/mac4lin)

---

### Post by sayakb on 2008-03-10
> **aysiu said:**
> Yes, it's a good habit to get into for graphical applications. Read this:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Okay.. Thanks for the info :)

---

### Post by Anduu on 2008-03-10
The only time you need to put themes in the /usr/share/themes folder is if you want it accessible to all users.
If the theme does not work in your /home/<username>/.themes folder it won't work in /usr/share/themes either.

As I stated before a lot of themes out there are not packaged correctly.Extract the theme and check the contents.The folder you want to move to /home/<username>/.themes should contain:

A gtk-2.0 folder ***and/or*** a metacity-1 folder ***as well as***  a file called index.theme

Also note that ***not all themes appear in the main theme selection window***.For a lot of themes you have to go into the customize tab and search for it in "controls" for a gtk theme or "window border" for a metacity theme.

---

### Post by JoseReyes on 2008-03-11
I want to thank youj guys for all the world of knowledge on this forum. It sure make my life a lot easy, as I am a newbie at linux. Big thank you to all of you guysss...  :)

---

