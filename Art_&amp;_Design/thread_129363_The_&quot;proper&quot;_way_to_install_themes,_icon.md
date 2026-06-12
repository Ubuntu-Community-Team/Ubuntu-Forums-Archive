---
title: "The &quot;proper&quot; way to install themes, icons, etc..."
date: 2006-02-13
forum: Art &amp; Design
---

### Post by raublekick on 2006-02-13
This has been bugging me for a while, and I figure this is the best place to ask.

What is the proper way to install themes, icons, and whatever else could fall into this category?

In the Gnome Theme Preferences you can just drag and drop a theme in there, and it installs. Great! But what about themes that come with multiple color versions? Or a GTK+ and a Metacity version? 

The .themes directory is where you can manually extract themes you want. Ok, got that, works pretty decent. 

Then there is the issue of themes not showing when you run stuff like Synaptic that requires sudo. I know there is somewhere to put themes so they show up here, but I forget where. Now, putting a theme in here makes it show up in Synaptic, et al, but if it goes in here from the beginning will it show up for normal users? I'm curious if this is where all themes should be sent since this is where Ubuntu installs them. 


Also, I often see themes that are presented on gnome-look as having multiple colors, but when you drag and drop into Theme Preferences you get one color. How do you get those other colors?

Thanks :)

---

### Post by bluevoodoo1 on 2006-02-13
[QUOTE=raublekick]Then there is the issue of themes not showing when you run stuff like Synaptic that requires sudo.[/QUOTE]

I am also wondering this. 

And also how to theme nautilus when running 'sudo nautilus' On my old computer I ran 'sudo gnome-theme-manager' to get themes for nautilus (when running as superuser) and it seemed to work, but not on this install....

---

### Post by senning on 2006-02-13
You can move theme folders into /usr/share/themes.  Generally, I'm too lazy, though.  Drag 'n Drop is pretty snazzy except for the couple minutes a day I need to look at Synaptic while it updates Dapper.  My experience is, as long as the theme folder is in there, choosing the theme through preferences works fine even for sudoed apps.

---

### Post by Lux Perpetua on 2006-02-13
When I noticed the sudo issue, I made ~root/.themes a symbolic link to .themes in my normal home directory :o
```
sudo ln -s ~/.themes /root/.themes
```I think that solved the problem. There are probably better ways.

---

### Post by raublekick on 2006-02-16
anyone else? anyone?

---

### Post by theturner on 2006-02-16
[QUOTE=raublekick]anyone else? anyone?[/QUOTE]
What part of your question is still unanswered?

---

### Post by Spark* on 2006-02-16
[QUOTE=raublekick] Now, putting a theme in here makes it show up in Synaptic, et al, but if it goes in here from the beginning will it show up for normal users? I'm curious if this is where all themes should be sent since this is where Ubuntu installs them. [/quote]
It doesn't matter, you can put all themes into /usr/share/themes if you want and it will work fine for all users. Your local .themes folder is just a lot more convenient because you can use drag and drop etc.


> Also, I often see themes that are presented on gnome-look as having multiple colors, but when you drag and drop into Theme Preferences you get one color. How do you get those other colors?
If they contain multiple versions in the tarball then you have to extract them manually to your themes folder, otherwise only one of them will be installed AFAIK. If it's a metacity theme then keep in mind that it adopts the color of your Gtk theme.

---

### Post by raublekick on 2006-02-16
Hmm... Ok, thanks Spark* I think that answered my question. 

So, that's like if I go into the theme details and set the controls to human, and the window decoration to clearlooks, I get a orange/brown clearlooks. Do the controls ultimately determine the color of the window decoration?

I'll have to download some more themes and give it a shot.

---

### Post by arctic on 2006-02-16
As already told, the themes (if they should be available for root and anyone else) should be stored in /urs/share/themes, the icons in /usr/share/icons, the wallpapers in /usr/share/wallpaper. That's all.

---

### Post by Spark* on 2006-02-16
[QUOTE=raublekick]So, that's like if I go into the theme details and set the controls to human, and the window decoration to clearlooks, I get a orange/brown clearlooks. Do the controls ultimately determine the color of the window decoration?[/QUOTE]
Yes, although some window decorations also hardcode their colors.

---

### Post by chopsbuntu on 2006-02-19
I must really be dumb or something, because for the life of me I cannot get a single theme to install. All I can do is download the darn things. After that, they just sit on my desktop.

Hate to say it, but I need step-by-step instructions from beginning to end. I'm using KDE 3.5.1 and when I right-click on one of the theme files, I do not get an option to extract the file. :-?

---

