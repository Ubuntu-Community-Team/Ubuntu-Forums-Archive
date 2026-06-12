---
title: "quick question about gnome-settings-daemon"
date: 2005-11-04
forum: Absolute Beginner Talk
---

### Post by super on 2005-11-04
is it possible to specify which gtk theme to use with the command line?
for example could i include in my .fvwm2rc file something like this:

[FONT="Courier New"]exec    gnome-settings-daemon -theme whatever-i-want[/FONT]

or if that is not possible, could i use something like gtktheme switch fromthe command line?

what i would like is to be able to specify different themes for different desktop environments. i want my gtk apps to match my FVWM theme/background when i am in FVWM without having to use the same theme when i log into gnome

---

### Post by Kyral on 2005-11-04
You mean like what the root uses (I assume you are talking about when you sudo an app from the commandline it looks different).

If you mean like spanning multiple DEs, then its mostly gonna be no. I mean some can be shared (XFCE and GNOME tend to have a good thing going on with themes), but its a crapshot. Most of the time you'd have to find one that looks like it for the other DE

---

### Post by super on 2005-11-04
here's an example:
in fluxbox or FVWM, my gtk apps look great with [this]("http://art.gnome.org/themes/gtk2/1064") theme because my wallpaper is dark.

but in gnome this theme looks terrible because it does not match the wall or the metacity controls. that mean that everytime i log into gnome after using fluxbox or FVWM, i have to open the theme preferences dialog and change it.

and when i head back to flux or FVWM after using gnome i need to switch themes back *again.*

if there was a way to change the themes using just the command line i could but the command in my .fvwm2rc file or my .fluxbox/init file and it could be done automatically.

---

### Post by Kyral on 2005-11-04
I have not actually heard of a way to do this....I mean if you knew what was changed in the files, you could make two copies of them and have a different one invoked when GNOME/FVWM started up....sorry....

---

### Post by super on 2005-11-04
[QUOTE=Kyral]I have not actually heard of a way to do this....I mean if you knew what was changed in the files, you could make two copies of them and have a different one invoked when GNOME/FVWM started up....sorry....[/QUOTE]

actually i think you got it! :razz: 
i want a different theme invoked depending on which destop environment was started.

...maybe this should be in the art talk section or something.

---

### Post by Wolki on 2005-11-07
[QUOTE=super]actually i think you got it! :razz: 
i want a different theme invoked depending on which destop environment was started.[/QUOTE]

You can set the theme using gConf. For example,
```
gconftool-2 --type String -s "/desktop/gnome/interface/gtk_theme" "Human"
```

will set your theme to Human, replace Human with another GTK theme name to use that.

IIRC gnome-settings-deamon sets up gconf automatically, so the only thing you have to do is set the theme afterwards with the line above. This will change the setting permanently, so add somnething like it to all DEs you use, with the respective themes.

---

### Post by super on 2005-11-11
^ thank you! it works perfectly! :D

---

