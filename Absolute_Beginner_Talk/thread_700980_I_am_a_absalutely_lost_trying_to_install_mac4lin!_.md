---
title: "I am a absalutely lost trying to install mac4lin! NEW to Ubuntu, please help!!!"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by virologynerd on 2008-02-18
Hi (1st post:KS)
I am a mac user who is trying to use ubuntu for the 1st time (on a previous ms xp) 
I downloaded mac4lin 0.4 and tried to to install it, I cannot (for the life of me) get past installing the theme (I know I'm pathetic:oops:) I was following these instructions: 
[http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac](http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac)
I am able to "customize" under themes so that it sorta looks like the theme but isn't the real thing:confused:,
basically when I hit "install" under preferences/appearances, I find the Mac4Lin GTK Metacity Theme .tar.gz file but cannot find a theme in the file, I have downloaded the mac4lin package many times from different sites so I know it is not that.
I am really frustrated ](*,) and would REALLY appreciate some help!!!!!:( 
Thanks!!!!

---

### Post by spiderbatdad on 2008-02-18
Just to make sure you know...the screenshot displayed on your link, is of one running opengl or compiz-fusion with kiba-dock (or maybe awn) installed. I  believe the mac4lin theme only offers some change in window borders and icons.

---

### Post by ice60 on 2008-02-18
this is the thread for it i think -
[http://ubuntuforums.org/showthread.php?t=555373](http://ubuntuforums.org/showthread.php?t=555373)

---

### Post by Sinkingships7 on 2008-02-18
> **spiderbatdad said:**
> Just to make sure you know...the screenshot displayed on your link, is of one running opengl or compiz-fusion with kiba-dock (or maybe awn) installed. I  believe the mac4lin theme only offers some change in window borders and icons.
mac4lin includes instructions and source lines to add to your repos to get kiba-dock.

as for getting it to work, i don't really know what to tell you... i installed that whole pack a few days ago, just to try it out, and i had no problems just reading off the instructions.

perhaps if you post the instructions you don't understand here, i can rewrite them for you so they make a little more sense?

---

### Post by stchman on 2008-02-18
> **virologynerd said:**
> Hi (1st post:KS)
I am a mac user who is trying to use ubuntu for the 1st time (on a previous ms xp) 
I downloaded mac4lin 0.4 and tried to to install it, I cannot (for the life of me) get past installing the theme (I know I'm pathetic:oops:) I was following these instructions: 
[http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac](http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac)
I am able to "customize" under themes so that it sorta looks like the theme but isn't the real thing:confused:,
basically when I hit "install" under preferences/appearances, I find the Mac4Lin GTK Metacity Theme .tar.gz file but cannot find a theme in the file, I have downloaded the mac4lin package many times from different sites so I know it is not that.
I am really frustrated ](*,) and would REALLY appreciate some help!!!!!:( 
Thanks!!!!

I have a tutorial for transforming your Gnome into OS X.

[http://www.stchman.com/transform_osx.html](http://www.stchman.com/transform_osx.html)

Hope this helps.

---

### Post by northern lights on 2008-02-18
Gotta agree - the picture includes a whole lot more than some wm theme. Provided that the pic displays about what is your aiming for, I'll attempt to give you a few easy-to-follow ideas:

Not for every step will it neccessarily matter, but it would have been beneficial toknow a few specs. I'll be assuming your running an Gutsy, i386, gnome, compiz-fusion.

First of changing your window manager theme might be indeed a good idea on your way to a mac os like ubuntu. Rather than sticking to the ubuntu default wm metacity you might want to consider emerald. To install, open a terminal and type:
```
sudo apt-get install emerald
```
A decent source for emerald themes (and all other sorts of eye-candy) is [gnome-look]("http://www.gnome-look.org") (emerald themes for your purpose are found under the "Compiz" menue entry. While you may certainly browse all, I'd recommend you check these links (first one might be what you can't install):
[http://gnome-look.org/content/show.php/Mac4Lin+ver.0.4+Emerald+Theme?content=71995]("http://gnome-look.org/content/show.php/Mac4Lin+ver.0.4+Emerald+Theme?content=71995")
[http://gnome-look.org/content/show.php/Aqua+aero.?content=72934]("http://gnome-look.org/content/show.php/Aqua+aero.?content=72934")
Click the download button and save to disk. Now run "emerald-theme-manager". Import the themes you just downloaded. If emerald doesn't take over as wm right away, run "emerald --replace" and you should be set.

Since your a Mac user, I suppose it can be safely assumed you don't want to do without the Expose feature of OS X - in compiz-fusion that's called Scale. In In order to further alter your background effects, go to "System > Preferences > Advanced Desktop Effects", or alternatively choose "System > Preferences > Appearance" and then click the "Preferences" button next to "custom" under the "Visual Effects" tab. Should neither be available, you have yet to install ccsm. In your terminal type:
```
sudo apt-get install compizconfig-settings-manager
```
Either way, in the Advanced Desktop Effect settings window you should scroll to the "Window Management" section and enable "Scale". You can click on it's icon to select  more options. Under the "Actions" you can change the key bindings. For mac like behaviour set "Iniate Window Picker for all windows" to TopRight screen edge. Play around with the speed slider until your happy - the others sliders you don't need to worry about too much.

Further, the dock in the picture appears to be cairo-dock - whatever it is, I'd say currently cairo-dock is in general the best dock in town and it's certainly the most mac like. To install the latest version of the dock, you need to download the following two deb-packages
[cairo-dock_v1.4.6.3_i686-32bits.deb]("http://prdownload.berlios.de/cairo-dock/cairo-dock_v1.4.6.3_i686-32bits.deb")
[cairo-dock-plug-ins_v1.4.6.3_i686-32bits.deb]("http://prdownload.berlios.de/cairo-dock/cairo-dock-plug-ins_v1.4.6.3_i686-32bits.deb")
The easiest way to install 'em is via the GDebi Package Installer. After clicking on the download link, simply choose "Open With" and select "GDebi". If that option does not exist first open your "Applications" menu and in "Add/Remove..." install GDebi.
With both packages installed, run "cairo-dock". Pick the "_Mac OSX_ theme, modify, add and remove launchers from there. An excellent source for icons would again be [gnome-look]("http://www.gnome-look.org")

[EDIT]
Had one more idea - you can change your firefox theme (probably woulda gotten that idea yourself), check out [firefox/addon/4927]("https://addons.mozilla.org/en-US/firefox/addon/4927")
[/EDIT]

Report on your progress and good luck!

---

### Post by virologynerd on 2008-02-19
wow thanks every one! the suggestions really helped!! especially "northen lights"!!! :popcorn:

---

### Post by virologynerd on 2008-02-19
"http://www.stchman.com/transform_osx.html " <---- this really helped too!!!

---

### Post by ajeetraj on 2008-02-21
Hey Northern lights...good job man! Very nice and easy how to :)

---

