---
title: "I did it!  Enlightenment"
date: 2005-10-08
forum: Absolute Beginner Talk
---

### Post by zerhacke on 2005-10-08
I did it!  I installed Enlightenment, got it to show up under gdm's login screen as a selectable window manager, and even put a new theme and wallpaper on it.  I even customized the user menu to reflect my personal system and tools I need to use on a regular basis.

It wasn't so hard.  Took a little bit of reading to figure out how to make it selectable at the login screen, and a little more to figure out how to customize the menus, but it wasn't hard.  Just read up on it.  Google is your friend, and this forum helped a lot too.

Finally, I did something that I didn't have to ask five questions on first.

For others who may need this in the future, here's a helper list of Enlightenment goodness.

First and foremost, apt-get will not set Enlightenment up to be a choice when logging in via gdm.  You must create a file, /usr/share/xsessions/Enlightenment.desktop to be precise.  Fill it with

```
[Desktop Entry]
Encoding=UTF-8
Name=E17
Comment=This session logs you into E17
Exec=/usr/local/bin/enlightenment
# no icon yet, only the top three are currently used
Icon=
Type=Application
```

Save the file. Logout.  Enlightenment should be selectable as a window manager now.

The first time I ran Enlightenment, I was at a loss as to how to run programs.  You must middle click, mouseover Maintenance, then click Regenerate Menus.  This will give you some new menu options such as the ability to start an Xterm.  Using your favorite editor you can edit the menus you are given.  Simply point your editor at ~/.enlightenment/user_apps.menu and edit away.

Took a little reading to figure it out, but the layout of the user_apps.menu file is as such.  The first statement in quotes is what you want the menu to say.  The NULL is to tell Enlightenment not to use an icon beside the program name.  Don't change the EXEC statement, as this executes the program you want to run.  The second statement in quotes is the program name you want to run.  So ```
"GAIM" NULL exec "gaim"
``` builds an entry to your user menu that says GAIM in all caps, and executes gaim the program.  It's simple once you get the hang of the syntax.  Oh, and the standard one it generates for you fills a lot of stuff in that you probably don't have installed on your system.  It's safe to leave them there if you want, because any program not found on the system will not display the corresponding menu entry.  So if you make a "My Program" NULL exec "foobar123xyzfakeprogramnotinstalled" entry, My Program will not be displayed on your user list unless you actually have foobar123xyzect.ect. installed on your system.

After you edit the user_apps.menu file, you need to regenerate the menus again.  It took me ten minutes to figure this out on my own.

There's lots of themes for E16.  To install them, you simply untar the theme file into ~/.enlightenment/themes/(nameoftheme)/ then restart Enlightenment.  Middle click and choose the theme you just installed.  I'll warn you, some of the themes out there put some buttons on the desktop that correspond to programs you may not have installed, and I havn't yet figured out how to get rid of those buttons or change the program they correspond to.  I havn't played with it yet either.

And, it seems I've forgotten how to put a wallpaper on E, so I'll have to get back to you on that.

Hope this helps other newbies.  I thought it would be useful to put all this information in one place.

---

### Post by Svictor on 2005-10-08
Thanks ! I'm just going through this myself. Don't know yet if enlightenment is for me but I'm happy to be able to give it a simple try. By the way, for me, synaptic created the entry in the gnome login options. I didn't know however how to fix the menus.

---

