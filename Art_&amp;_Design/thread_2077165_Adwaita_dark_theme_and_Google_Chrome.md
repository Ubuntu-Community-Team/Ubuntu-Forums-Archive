---
title: "Adwaita dark theme and Google Chrome"
date: 2012-10-27
forum: Art &amp; Design
---

### Post by x-shaney-x on 2012-10-27
I have set the dark variation of Adwaita to be used for all apps via gnome tweak tool and it looks great.
Unfortunately, there is one app that doesn't follow the theme and stands out like a sore thumb:  Google Chrome.

Any way to get Chrome to use the theme or anyone know of any Chrome themes to match it?

---

### Post by consolation on 2012-10-29
Does going into Chrome's settings and selecting "Use system title bar and borders," not give you the look you want?

---

### Post by x-shaney-x on 2012-10-29
No, it just makes it use the regular, light Adwaita theme.

---

### Post by vasa1 on 2012-10-29
> **x-shaney-x said:**
> I have set the dark variation of Adwaita to be used for all apps via gnome tweak tool and it looks great.
Unfortunately, there is one app that doesn't follow the theme and stands out like a sore thumb:  Google Chrome.

Any way to get Chrome to use the theme or anyone know of any Chrome themes to match it?
I don't like Adwaita because much of it isn't available for inspection. Anyway, could you put up an image of an app that you like and of Chrome? In the case of Chrome, I suggest you go into settings and ensure that "use GTK+ theme" is active and turn off "use system title bar and borders". Then put up that image.
Also, do you have a file called chromium.rc in your theme folder?

---

### Post by x-shaney-x on 2012-10-29
I have attached a screenshot of the desktop with nautilus using the dark theme enabled for all and the way chrome displays with the standard theme.
This is with gtk theme and borders enabled.

There is not a downloaded theme.
Gnome 3.6 uses a dark variation of the default theme for some apps (such as totem) and I have simply enabled an option in gnome tweak tool to enable that theme for all apps.

---

### Post by vasa1 on 2012-10-29
> **x-shaney-x said:**
> I have attached a screenshot of the desktop with nautilus using the dark theme enabled for all and the way chrome displays with the standard theme.
This is with gtk theme and borders enabled.

There is not a downloaded theme.
Gnome 3.6 uses a dark variation of the default theme for some apps (such as totem) and I have simply enabled an option in gnome tweak tool to enable that theme for all apps.

In the GNOME world, there are two main types of apps: gtk2 and gtk3. Nautilus is an example of a gtk3 app. Chrome isn't. So a theme that applies to Nautilus may not apply wholly or partly to a gtk2 app. Chrome is largely gtk2. So is Synaptic (if you have it installed).

Consequently, Chrome's style is determined by the contents of the gtkrc and chromium.rc files.

---

### Post by sgo. on 2012-11-07
You need to install ```
gtk2-engines-murrine
``` to make Chrome look a little nicer in Gnome3.

---

### Post by Fitoschido on 2012-11-07
The "Dark theme for all apps" setting only applies for GTK+3 applications. As Chrome is a GTK+2 application, your only option is to create a dark theme for it, or ask someone to create it for you.

---

### Post by olligobber on 2012-11-09
You can create a theme for Chrome using tools such as this one -> [http://www.themebeta.com/chrome-theme-creator-online.html](http://www.themebeta.com/chrome-theme-creator-online.html)
By taking images from your dark theme and disabling system borders it should fit in well.

---

