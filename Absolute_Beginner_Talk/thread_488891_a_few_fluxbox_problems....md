---
title: "a few fluxbox problems..."
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by crash0 on 2007-06-30
hello,

i just moved from gnome to fluxbox and i can see the difference in speed (my laptop is old and slow...)
it looks great for now, but i'm interested in a few things with making my fluxbox a bit better. so, here it goes:

1. how to add a wallpaper (and make it load at startup)?

2. how to add icons?

3. how to add stuff to the bar at the bottom? can i add a button that would call up the main menu? can i add icons to the bar?

4. how to edit programs displayed in the menu? i saw somwhere that you're supposed to run update-menus after installing fluxbox, but now some of my programs aren't displayed and some which are displayed aren't even installed...

5. what's up with rox filer? i couldn't work out how to cut-paste files (only copy-paste) and it seems that it doesn't send files to the trash but deletes them... anyway, it looks a bit weird to me, so i'd like to use nautilus instead for now... do i have to make nautilus default or something like that?

6. how to make the desktop display files contained in the ~/Desktop folder?

that's about it for now, thanks in advance ;)

---

### Post by overdrank on 2007-06-30
> **crash0 said:**
> hello,

i just moved from gnome to fluxbox and i can see the difference in speed (my laptop is old and slow...)
it looks great for now, but i'm interested in a few things with making my fluxbox a bit better. so, here it goes:

1. how to add a wallpaper (and make it load at startup)?

2. how to add icons?

3. how to add stuff to the bar at the bottom? can i add a button that would call up the main menu? can i add icons to the bar?

4. how to edit programs displayed in the menu? i saw somwhere that you're supposed to run update-menus after installing fluxbox, but now some of my programs aren't displayed and some which are displayed aren't even installed...

5. what's up with rox filer? i couldn't work out how to cut-paste files (only copy-paste) and it seems that it doesn't send files to the trash but deletes them... anyway, it looks a bit weird to me, so i'd like to use nautilus instead for now... do i have to make nautilus default or something like that?

6. how to make the desktop display files contained in the ~/Desktop folder?

that's about it for now, thanks in advance ;)

Hi maybe this will help 
[http://fluxbox.org/docbook/en/html/](http://fluxbox.org/docbook/en/html/)
Good luck!:popcorn:

---

### Post by RedSquirrel on 2007-06-30
To set the background, you'll probably have to install a wallpapersetter program. Check to see what this command reports:

```
fbsetbg -i
```

It should report: "program_name is a nice wallpapersetter. You won't have any problems." If it says something else, install feh:

```
sudo apt-get install feh
```Find the line in your ~/.fluxbox/init that looks like this:

```
session.screen0.rootCommand:
```and change it to 

```
session.screen0.rootCommand: fbsetbg -l
```That will ensure that the last wallpaper you set will be loaded at startup.

To set the background:

```
fbsetbg -f path_to_background
```Do 

```
fbsetbg -h 
```to see your other options.

Add something similar to this to your menu so that you'll have a list of backgrounds in your menu that you can just click:

```
 [submenu] (Backgrounds)
  [wallpapers] (~/.fluxbox/backgrounds)
  [wallpapers] (~/path_to_more_wallpapers)
 [end]

```I'll leave the stuff about icons and so on to someone else since I don't use desktop icons at all. I don't use rox either.

See the links in my signature for more information and don't forget to search the forums for more details on Fluxbox.

For a more complete menu, try 'Method B' from the first link in my signature.

The Fluxbox man page is also quite helpful:

```
man fluxbox
```Have fun. :D

---

### Post by kerry_s on 2007-07-01
> **crash0 said:**
> hello,

i just moved from gnome to fluxbox and i can see the difference in speed (my laptop is old and slow...)
it looks great for now, but i'm interested in a few things with making my fluxbox a bit better. so, here it goes:

1. how to add a wallpaper (and make it load at startup)?

2. how to add icons?

3. how to add stuff to the bar at the bottom? can i add a button that would call up the main menu? can i add icons to the bar?

4. how to edit programs displayed in the menu? i saw somwhere that you're supposed to run update-menus after installing fluxbox, but now some of my programs aren't displayed and some which are displayed aren't even installed...

5. what's up with rox filer? i couldn't work out how to cut-paste files (only copy-paste) and it seems that it doesn't send files to the trash but deletes them... anyway, it looks a bit weird to me, so i'd like to use nautilus instead for now... do i have to make nautilus default or something like that?

6. how to make the desktop display files contained in the ~/Desktop folder?

that's about it for now, thanks in advance ;)



1. follow RedSquirrel's guide
2. rox-filer
3. no
4. (your editor) ~/.fluxbox/menu
5. rox takes getting use to, but can do alot. just add nautilus --no-desktop to your menu
6. rox-filer

Sounds like you should be running xfce4 instead, has all those features stock.

---

### Post by RedSquirrel on 2007-07-01
> **kerry_s said:**
>  Sounds like you should be running xfce4 instead, has all those features stock.

That's a great suggestion. Sometimes it's nice to use something that includes everything you need so you don't have to jump through so many hoops. :)

---

### Post by kerry_s on 2007-07-01
> **RedSquirrel said:**
> That's a great suggestion. Sometimes it's nice to use something that includes everything you need so you don't have to jump through so many hoops. :)

So many people get told to try xubuntu, but they can skip all that and just run xfce4 by itself, depending on how you set it up it can be just as fast as fluxbox. I even was running a combination fluxbox+thunar which has the xfce4-panel as a dependency so you can use that in fluxbox to, with or without the fluxbox panel. i was going to recommend that fbpanel, but i tried it and it sucks, when it come to ease of setup.
anyways to each there own, hope he finds something he can live with. ;)

---

### Post by kerry_s on 2007-07-01
Oh,  RedSquirrel
 i been meaning to ask you, can i get a peek at your ~/.fluxbox/keys file? i'm still setting mine up and haven't decided what way to go. :(

i'll show you mine, if you show me yours ;) thanks

```
OnDesktop Mouse1 :HideMenus
OnDesktop Mouse2 :WorkspaceMenu
OnDesktop Mouse3 :RootMenu

Mod1 F2 :Exec fbrun -font Sans-16 -w 500 -h 50 -pos 250 350
None Print :Exec scrot %T.jpg

Mod4 m :RootMenu
Mod4 w :WorkspaceMenu
Mod4 s :ShowDesktop
Mod4 Delete :Exec xkill

Control F3 :Exec aumix -v -5
Control F4 :Exec aumix -v +5

Control F5 :Exec spicctrl -b0
Control F6 :Exec spicctrl -b255

Control Mod1 Delete :Exec sudo /sbin/reboot


```

---

### Post by RedSquirrel on 2007-07-01
> **kerry_s said:**
> So many people get told to try xubuntu, but they can skip all that and just run xfce4 by itself, depending on how you set it up it can be just as fast as fluxbox. 

I've been thinking about trying the latest Xfce (not Xubuntu!). Maybe one of these days...


> **kerry_s said:**
> I even was running a combination fluxbox+thunar which has the xfce4-panel as a dependency so you can use that in fluxbox to, with or without the fluxbox panel. i was going to recommend that fbpanel, but i tried it and it sucks, when it come to ease of setup.

I tried fbpanel a while ago but I didn't think it was all that great. I played around with the configuration file for some time but in the end I just dropped it.

I am off panels altogether now. I have spent a fair bit of time in front of the computer today with a setup like the screenshot I posted above and I'm lovin' it. (I reduced the fbpager to 125x32 which for me is usable, yet unobtrusive.)

The thing that really has me jazzed is that I got lm-sensors to show my CPU temp and fan speed. acpi is buggy for me so that was a no-go. My one-line conky is really making me happy. :D



> **kerry_s said:**
> Oh,  RedSquirrel
 i been meaning to ask you, can i get a peek at your ~/.fluxbox/keys file? i'm still setting mine up and haven't decided what way to go. :(

i'll show you mine, if you show me yours ;) thanks


:oops::lol: 

Here it is as of right now. I should tinker with this some more, but here goes...

```
!mouse actions added by fluxbox-update_configs
OnDesktop Mouse1 :hideMenus
OnDesktop Mouse2 :workspaceMenu
OnDesktop Mouse3 :rootMenu

Control Mod1 Left :PrevWorkspace
Control Mod1 Right :NextWorkspace
Mod1 Tab :MacroCmd {Deiconify LastWorkspace} {NextWindow 0}
Mod1 F1 :Workspace 1
Mod1 F2 :Workspace 2
Mod1 F3 :Workspace 3
Mod1 F4 :Workspace 4
Mod1 F5 :ExecCommand xterm
Mod1 F6 :ExecCommand leafpad
Mod1 F7 :ExecCommand abiword 
Mod1 F8 :ExecCommand oowriter
XF86HomePage :ExecCommand firefox
XF86Mail     :ExecCommand mozilla-thunderbird
XF86Search   :ExecCommand gksudo synaptic
XF86AudioMute :Exec aumix -v 0 
XF86AudioLowerVolume :Exec aumix -v -5
XF86AudioRaiseVolume :Exec aumix -v +5
Print :Execute import -pause 7 -window root ~/misc/screenshots/screenshot-`date +%Y-%m-%d_%T`.jpg
Mod1 Sys_Req :Execute import -frame ~/misc/screenshots/window-`date +%Y-%m-%d_%T`.jpg
Super_L :RootMenu
Super_R :RootMenu
```

---

### Post by kerry_s on 2007-07-02
thanks RedSquirrel,
 your stuff always gives me ideas. i did the opposite of you, i kept the toolbar and got rid of fbpager. it's easy enough to call the workspace menu(mod4 w) to see what i have running on what desk. i also only have 1 desktop and just use the "new workspace" when i need more.

here's what i settled on for now.

```
OnDesktop Mouse1 :HideMenus
OnDesktop Mouse2 :WorkspaceMenu
OnDesktop Mouse3 :RootMenu


Mod1 F2 :Exec fbrun -font Sans-16 -w 500 -h 50 -pos 250 350

Mod4 m :RootMenu
Mod4 w :WorkspaceMenu
Mod4 s :ShowDesktop
Mod4 t :ToggleDecor
Mod4 Delete :Exec xkill

Control F3 :Exec aumix -v -5
Control F4 :Exec aumix -v +5

Control F5 :Exec spicctrl -b0
Control F6 :Exec spicctrl -b255

Control Mod1 Delete :Exec sudo /sbin/reboot

Print :Exec scrot %T.jpg
Home :Exec emelfm

F1 :Exec iceweasel
F2 :Exec xlinks2 google.com
F3 :Exec pidgin

F12 :Exec xterm

```

---

### Post by the bored majority on 2007-07-02
**@red**

i've been following your threads and such on fluxbox and must say thank you. these have helped me alot. coming from a Litestep shell on windows i was looking for a similar setup on ubuntu. this fits nicely.

i just had one questions; why does this set the background?

```
   [submenu] ([backgrounds])
      [wallpapers] (/usr/share/backgrounds)
   [end]
```

all this does is list the pics in that particular folder, why does just simply clicking it set it as the background?

just curiosity :)

---

### Post by bodhi.zazen on 2007-07-02
From the Fluxbox wiki :> [wallpapers] (directory)
   This allows you to list your backgrounds. This tag is built in to use 
   fbsetbg(1) and allows you to simply click on an image to set your 
   wallpaper. See? Fluxbox makes it easy…

[http://fluxbox-wiki.org/index.php/Howto_edit_menu](http://fluxbox-wiki.org/index.php/Howto_edit_menu)

[http://fluxbox-wiki.org/index.php/Fluxbox-wiki](http://fluxbox-wiki.org/index.php/Fluxbox-wiki)

---

### Post by RedSquirrel on 2007-07-03
> **kerry_s said:**
> thanks RedSquirrel,
your stuff always gives me ideas. 

No problem. I've borrowed a lot of your ideas too. :)

> **kerry_s said:**
> i did the opposite of you, i kept the toolbar and got rid of fbpager. it's easy enough to call the workspace menu(mod4 w) to see what i have running on what desk. i also only have 1 desktop and just use the "new workspace" when i need more.

That's interesting. I usually have between four and six workspaces. ;)

> **kerry_s said:**
>  here's what i settled on for now.

Looks good. I see you've gone back to scrot.


> **the bored majority said:**
> @red

i've been following your threads and such on fluxbox and must say thank you. these have helped me alot. coming from a Litestep shell on windows i was looking for a similar setup on ubuntu. this fits nicely.

Glad I was able to help.

> **the bored majority said:**
> i just had one questions; why does this set the background?

I'm too late... bodhi.zazen has answered this very well. :D

You can also add a command. At one point I had something like:

```
[submenu] ([backgrounds])
    [wallpapers] (/usr/share/backgrounds) {fbsetbg -t}
[end]

```because I was using a lot of "tiled" backgrounds. Without the "-t" option, fbsetbg stretched one tile to fit the entire screen!

---

### Post by jviscosi on 2007-07-04
> **crash0 said:**
> hello,

3. how to add stuff to the bar at the bottom? can i add a button that would call up the main menu? can i add icons to the bar?



If you really want to have a button to call up the menu, there is a program called ftmenu that puts an icon in your system tray that, when clicked, calls up your Fluxbox menu.  You can find it [here]("http://ftmenu.sourceforge.net/").

I haven't used this application in quite a long time.  As I recall, it didn't recurse into submenus, so I edited the code to make it do so.  Even then it didn't know what to make of special Fluxbox actions like Exit, so it's kind of limited.  It may or may not have been improved since I ran it.

---

### Post by RedSquirrel on 2007-07-04
> **jviscosi said:**
> If you really want to have a button to call up the menu, there is a program called ftmenu that puts an icon in your system tray that, when clicked, calls up your Fluxbox menu.  You can find it [here]("http://ftmenu.sourceforge.net/").

I haven't used this application in quite a long time.  As I recall, it didn't recurse into submenus, so I edited the code to make it do so.  Even then it didn't know what to make of special Fluxbox actions like Exit, so it's kind of limited.  It may or may not have been improved since I ran it.
I stumbled upon *ftmenu* the other night while looking up some other Fluxbox stuff. I was going to add it to this thread but I forgot... glad someone else came along to add it. ;)

---

