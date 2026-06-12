---
title: "How do i install themes? [Resolved]"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by Guus on 2007-02-26
as the title says: hwo do i install themes?:D

ive downloaded [this](http://gnomelook.org/content/show.php?content=48752) theme.

But every time i drop it in the theme manager i get a file format error.

ive tried to drop both the folder and the tar.gz archive in the theme manager


Thanks in advance :)


~Guus

---

### Post by v8YKxgHe on 2007-02-26
This happens sometimes, if you extract the tar.gz file (which you've already done I take it), then copy the folder over to ~/.themes. 

"~/" means you're home directory. It's basicaly a shorthand way of typing "/home/username/" then the ".themes" section means in the folder "theme" but the full stop/period before it means it's a hidden file that you can not see normally. 

In the file browser go to View->Show Hidden Files, then you should see the "themes" folder. Just copy it into there and then select the theme via "System->Prefs->Theme"

Edit: Sorry, I didn't check the link out and didn't see it was a GDM theme. I'm never installed one so I'm not sure, sorry.

---

### Post by Crooksey on 2007-02-26
System > Administration > Login Window

Select a themed login, then point the browser to the theme archive.

Login window themes are different than GTK/Metacity themes.

---

### Post by aysiu on 2007-02-26
The theme your'e trying to install is a GDM theme. Those are for changing the login screen, not the look and feel of your desktop.

Go to System > Administration > Login Window > Install Theme to install it.

---

### Post by Sbarton on 2007-02-26
I've had the same problem with GDM themes. You could still use the Splash/Wallpaper though.
regards

---

### Post by Guus on 2007-02-26
> This happens sometimes, if you extract the tar.gz file (which you've already done I take it), then copy the folder over to ~/.themes.

"~/" means you're home directory. It's basicaly a shorthand way of typing "/home/username/" then the ".themes" section means in the folder "theme" but the full stop/period before it means it's a hidden file that you can not see normally.

In the file browser go to View->Show Hidden Files, then you should see the "themes" folder. Just copy it into there and then select the theme via "System->Prefs->Theme"

Edit: Sorry, I didn't check the link out and didn't see it was a GDM theme. I'm never installed one so I'm not sure, sorry.
__________________

i did what you said, but i still cant see the theme in the Theme Preferences window


EDIT: The rest of the suggestions worked, thx all :D

---

### Post by v8YKxgHe on 2007-02-26
Yeah, that's because I ddin't check the link out before I posted. I thought you meant a Metacity/GTK2 theme, not a GDM one so my way wouldn't have worked for a GDM theme.

---

