---
title: "launching programs that aren't in app menu"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by notld223 on 2006-08-15
ok... so I have a LOT of programs installed but I can't figure out how to launch them because stuff like wine and bittorrent aren't in any of the application submenus.... so i was wondering if anybody had any ideas on how to do this. (you probably know how though). Help would be appreciated...

---

### Post by anasofiapaixao on 2006-08-15
You have three kinds of programs that fall into this situation.
One, they were pre-installed but they menu entry is hidden: the all-knowing ubuntu folks decided for it to be that way. You can't imagine how frustrating the experience of getting to know how to edit gnome menus was for me. It took me tons of time to realize it was so simple: Either right click the application menu and choose "Edit Menus" or go to apps--> accessories --> alacarte menu editor. There you can unhide them.

Second, you installed them but the little brats didn't create a menu entry. On that situation you have to add an entry yourself: choose an icon, choose a name, and put the command. THIS IS VERY IMPORTANT: DON'T choose "link" on type. It shold be "application" as the default states. and what you are entering in "command" field is what you would enter if you were launching the app from the command line. Most of the apps can be accessed by just typing their package name; try on the cmd to type "firefox", "gaim", "ooo-writer", etc... this is because a link in /usr/bin is created with the name you have to type. Check this folder out if need to know an app's link. 

Third, any newbie's nightmare... THE COMMAND-LINE. Some programs don't have an entry simply because they don't have a GUI (Graphical User Interface). The most popular case of people-puzzling is - yeah, you guessed it - wine. You can, tough, out a link to "winecfg" - the wine configuration editor, that is graphical. In order to run windows binaries under wine, just do this:
- Get a windows executable. Any.
- Right click it and choose "Properties"
- Go to "open with" tab.
- Click "+ add" Probably wine won't be listed, so click on "use custom command" and type "wine" (just that, wine). Close all that stuff and it should be up and running.

Good luck in switching to Ubuntu!

---

### Post by kaens on 2006-08-15
Launch a terminal and type in the program name. Bittorrent will either be btdownload<something> (you probably want btdownloadgui) - just type in bt and hit the TAB button a few times. You can also use a client like Azeurus for bittorrent.

---

### Post by catlett on 2006-08-15
Some people like it, some don't but I love the Debian menu. Ubuntu is based on Debian but the Ubuntu devs have kept the Debian mneu out of the gnome menu. The Debian lists all your applications and services (I guess I should say "appears" to because I do not know for sure but everything I ever looked for was there).
When you enable it, it will be an entry in the Gnome menu under Applications. 
The setup is a little tricky because of alacarte menu editor but here are the steps.
Open up the terminal and enter 
```
sudo apt-get install menu
```
```
sudo apt-get install menu-xdg
```
```
killall gnome-panel
```
```
update menus
```
Now check for an entry titled "Debian" under applications. If it iosn't there then go to Applications<Accessories<Alacarte menu editor and select/highlight "applications". On the right will be the list of applications that can be enabled under applications. Make sure Debian is checked off.

That should be it. Actually all you use to do was install menu and it appeared but for some reason the debian menu is hard to install in dapper.

If it installs I think you will like it. At least you can see all your apps in one menu.

---

### Post by mostwanted on 2006-08-15
Even though Ana (sorry, I'm not gonna write the whole username :p) made a very good explanation on how to create menu shortcuts, you should know that the actual executables or links to them can be found in various places of your harddrive, but usually it's in /usr/bin. Games notably go into /usr/games.

---

### Post by anasofiapaixao on 2006-08-15
I just use this name because a) It's unlikely to be already registered anywhere (no luck with skype tho - that anasofiapaixao is not me) , b) I'm lazy and I don't want to remember tons of different usernames for all the things I register in and c) Nowadays just plain using your name instead of a nickname is original as most people don't do it :D

Plus it gets awkward to be treated by your nickname when it is just your names glued together - much nicer to be simply treated by Ana.

I just didn't mention that for not going in too much detail and write a will instead of a post as I tend to do; as it is unlikely he'll need so soon stuff out of the repos that is so unstandard to the point of not creating a link/placing the binary in /usr/bin. So far the only program I had this issue was SOK, but it's still in a development version so it's no example.

*[I really speak too much]*

---

### Post by meshica7 on 2006-08-15
Cattlet

Your codes work escept that when I type in "update menus" I get a "Command Not Found".
Any ideas?

Juan

---

### Post by catlett on 2006-08-15
> **meshica7 said:**
> Cattlet

Your codes work escept that when I type in "update menus" I get a "Command Not Found".
Any ideas?

Juan

Did you use the hyphen? It should work. It isn't anything that gets added. It is a way to update menu entries. Try it again and copy/paste it to be sure.
Also do not use sudo. You want to update your menu as a user.
```
update-menus
```

---

### Post by anasofiapaixao on 2006-08-15
Maybe it is "update-menus"?

EDIT: Lol... what are the chances of two people posting at the same thread in the exact same minute?

---

### Post by 3rdalbum on 2006-08-16
> **anasofiapaixao said:**
> Maybe it is "update-menus"?

EDIT: Lol... what are the chances of two people posting at the same thread in the exact same minute?

Pretty good, it happens to me at least once a week!

Also, with Wine: When you install Wine, I believe it sets up Ubuntu so that it recognises .exe files as being executable, and automatically opens them in Wine. In any case, that's what seemed to happen to me.

Only double-click a Windows program if you know it runs on Wine. When trying a Windows program for the first time, launch the program with Wine on the terminal. This way you will see if Wine gives you a "missing DLL" error message that will help you track down a native DLL file.

---

### Post by meshica7 on 2006-08-16
I'll give it a shot and let ya know how it goes.Thanx!

Juan

---

