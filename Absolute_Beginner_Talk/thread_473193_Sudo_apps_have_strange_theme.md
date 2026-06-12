---
title: "Sudo apps have strange theme"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by SnakeByte29 on 2007-06-13
I recently changed the desktop theme on my PC and now whenever I open a program that needs admin privaleges (Synaptic, for example) it has a weird, old-looking theme (reminiscent of Win9x). Is there a way to correct this behavior? 

Oh, I should note, I tried "sudo gnome-theme-manager" and it claims to not be able to load a daemon, which may cause a problem.

---

### Post by RomeReactor on 2007-06-13
Hi. That has also happened to me while using certain themes. I think it's a problem with the theme itself, rather than a problem with applications that require sudo, since using other themes works perfectly; this tends to happen with some themes downloaded from sites like [Freshmeat]("http://themes.freshmeat.net/"), [Gnome-look]("http://www.gnome-look.org/"), [Gnome Art]("http://art.gnome.org/"), and a few you can install through Synaptic. I suggest you use another theme, one that you can confirm that works well with most (if not all) applications, unless you're too attached to the one you're currently using (in which case, I don't think there's anything left to do except bear with its GTK glitches). Personally I like Clearlooks' ability to be customized, and it plays well with Synaptic, Firestarter, and other administration programs.

---

### Post by mgmiller on 2007-06-13
You can change the behavior.  It can be done a few different ways.  See the post linked to  here for instructions.   (Personally, I like having the root icons different, it reminds me that I am running in root, especially if I run a root nautilus.  It keeps me from doing something stupid.)

[http://ubuntuforums.org/showthread.php?t=422389&highlight=change+root+theme]("http://ubuntuforums.org/showthread.php?t=422389&highlight=change+root+theme")

---

### Post by testube_babies on 2007-06-13
These simple commands should remedy the situation:
```
sudo cp -R ~/.themes/* /usr/share/themes/
sudo cp -R ~/.icons/* /usr/share/icons/
```

The problem arises because the root account doesn't know to look inside your home folder to find the theme and icon files that you are using.  These commands copy your custom (installed) themes and icons to a well-known location for all accounts.

---

### Post by testube_babies on 2007-06-13
Also, I noticed that you issued the command "sudo gnome-theme-manager".  When using a graphical program in root mode, you should issue the "gksudo" command instead of "sudo".  Most of the time using sudo doesn't cause any problems, but I always use gksudo just in case.  More info here:
[http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

### Post by mcduck on 2007-06-13
> **testube_babies said:**
> These simple commands should remedy the situation:
```
sudo cp -R ~/.themes/* /usr/share/themes/
sudo cp -R ~/.icons/* /usr/share/icons/
```

The problem arises because the root account doesn't know to look inside your home folder to find the theme and icon files that you are using.  These commands copy your custom (installed) themes and icons to a well-known location for all accounts.

If you do it that way, you'll have to redo it every time you install new themes or icons. It's easier to instead just create symlinks:

```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
```
This way root user will always have same theme and icons you are using. :) (Of course if there are many users with admin rights then it might be nicer to just copy those theme files into /usr/share/themes so that all admins get nice root apps.)

---

