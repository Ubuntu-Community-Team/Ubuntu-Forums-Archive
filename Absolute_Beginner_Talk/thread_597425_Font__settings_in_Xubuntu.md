---
title: "Font  settings in Xubuntu"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by Dwood108 on 2007-10-30
I have just installed xubuntu gutsy and am trying to get the font settings to my liking.
I am using a 800x640 resolution as I only have a 15in monitor.
The problem is that the system settings don't seem to match the application settings in firefox or thunderbird.
When is set the font size in user interface settings to 9 it looks fine in the taskbars and application menu but way too small on the menus in firefox and thunderbird.
Does anyone know how to match these up?

Also if a try a font size of 8 it becomes practically unreadable.

---

### Post by henklaak on 2007-10-31
Firefox has it's own preference settings for fonts.

Edit->Preferences->Content->Fonts&Colors.

---

### Post by Dwood108 on 2007-10-31
Those preferences only affect the display of webpages, not the menus, toolbars etc of the programme itself.

Actually this does not seem to just effect firefox but other applications as well such as Abiword and Thunar. At a font size of 8 with resolution of 800x640 the fonts display very poorly.

---

### Post by kerry_s on 2007-10-31
why not just use the standard 1024x768, but make the things larger, as in bigger fonts, increase the size of the toolbar, icons, etc...
most linux applications aren't setup up for 800x600.

---

### Post by eeried on 2007-11-07
> why not just use the standard 1024x768

If the screen or the graphic are unable to deal with this resolution, what can Dwood108 do?

Well at least, Dwood108, you're lucky your app windows aren't too big for the screen as in my caes on an old  amd-k62 box.

---

### Post by mivo on 2007-11-07
You can change the fonts that Firefox uses for menus and such in the file:

/home/<username>/.mozilla/firefox/<profile>.default/chrome/userChrome.css

If it does not exist, create it and add these lines:

```

/* Global UI font */
* { font-size: 10pt !important;
  font-family: DejaVu Sans Book !important; 
} 

```

Just replace the font size and the font family with your preferences. The same also works in Thunderbird. You can use this file to be even more specific, but I think this will do what you want to achieve. :)

---

