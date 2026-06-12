---
title: "Themes screw up text in firefox?"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by Gorthus on 2007-04-16
I have just changed my theme, and it seems along with the panels and windows, it also edits the text of firefox pages...

Most of the sites I visit have white backgrounds, and this theme changed the font color to white, so I can't read anything!

What should I do?

---

### Post by Happy_Man on 2007-04-16
Which theme is this?

---

### Post by kerry_s on 2007-04-16
You can use a userchrome.css to change the font color.
-> [http://www.mozilla.org/unix/customizing.html](http://www.mozilla.org/unix/customizing.html)

---

### Post by Gorthus on 2007-04-16
> **Happy_Man said:**
> Which theme is this?

Neutronium-Gtk2

---

### Post by ComplexNumber on 2007-04-16
> **Gorthus said:**
> I have just changed my theme, and it seems along with the panels and windows, it also edits the text of firefox pages...

Most of the sites I visit have white backgrounds, and this theme changed the font color to white, so I can't read anything!

What should I do?
download [this]("http://gnome-look.org/content/show.php/Kore-GTK?content=55744") theme. its a dark theme that would otherwise have suffered from  'dark-theme-syndrome'(ie having the background to transparent webpages and the backgrounds of text entry areas set in black). inside, you will find instructions about how to change it so that firefox doesn't suffer from 'dark-theme-syndrome'. it worked for me.

---

### Post by kerry_s on 2007-04-16
> **Gorthus said:**
> Neutronium-Gtk2

I use to use that, it has instructions, did you read them?

```

Installation:
-------------
Open "System -> Preferences -> Theme" and drop the .tar.gz into the Theme Preferences window.


Low Contrast:
-------------
If you want to use the old low contrast version (light grey text) open a terminal and type:

cd $HOME/.themes/Neutronium-Gtk2/gtk-2.0/

mv gtkrc gtkrc_high_contrast

mv gtkrc_low_contrast gtkrc



Fixes:
------
Here are some fixes for common problems using the Neutronium Gnome theme package. (Or any dark Gnome theme for that matter)

It includes instructions for:

- Firefox

- Gaim

- Open Office 2

- Ubuntu


Firefox:
--------
If web forms and controls appear dark and unreadable you need to edit the css files that Firefox uses. The file location may vary on different linux distributions. Do the following in a terminal:

1. Backup the original file:
sudo mv /usr/lib/firefox/res/forms.css /usr/lib/firefox/res/forms_backup.css

2. Replace it with the provided forms.css
sudo mv "downloaded location"/GTK2/forms.css /usr/lib/firefox/res/forms.css

3. Then you need to edit html.css:
sudo gedit /usr/lib/firefox/res/html.css

Around line 60, change:

body {
  display: block;
  margin: 8px;
}

To:

body {
  background-color: white;
  color: black;
  display: block;
  margin: 8px;
}

Save the file, then restart Firefox, and you should have standard colours.


Gaim 2:
-------
To make Gaim use white fonts in conversations instead of the normal black, do the following in a terminal:

1. gedit $HOME/.gaim/prefs.xml

2. Around line 364 (probably) change the line:

<pref name='fgcolor' type='string' value=''/>

To:

<pref name='fgcolor' type='string' value='#FFFFFF'/>

Save the file. (restart Gaim if it's running)


Open Office 2:
--------------
For dark themes Open Office 2 uses a high contrast icon theme (due to automatic icon settings). If you don't like this, do the following:

1. Open Tools -> Options dialog

2. Go to OpenOffice.org -> View

3. Change the icon theme from automatic/null to a different one.


Ubuntu:
-------
If you are using Ubuntu and buttons look wierd, it's necessary to install the package "gtk2-engines-pixbuf” (sudo aptitude install gtk2-engines-pixbuf). This same recommendation is valid for all the themes based on engine "pixmap".


```

---

### Post by Gorthus on 2007-04-16
nevermind guys.. I'll just use another theme.

---

### Post by kerry_s on 2007-04-17
Just make sure you open them up to check if there's a read me file or instructions. You just double click on the downloaded file and the extractor will open or you can just right click it and select extract here.

---

### Post by DarKmaN-07 on 2007-04-24
Well they've explained the hard way to you, and you opted to use another theme, 

BUT: the easy way would have been to navigate to Firefox's Edit/Preferences/Content/Fonts & Colors/ 

There you could have told the browser not to implement the systems color scheme, but to override it with your default settings of Black text on a white background. 

For next time hey ;)

---

### Post by ComplexNumber on 2007-04-26
> **DarKmaN-07 said:**
> Well they've explained the hard way to you, and you opted to use another theme, 

BUT: the easy way would have been to navigate to Firefox's Edit/Preferences/Content/Fonts & Colors/ 

There you could have told the browser not to implement the systems color scheme, but to override it with your default settings of Black text on a white background. 

For next time hey ;)
tried that ages ago. it doesn't solve the problem. various websites will still have a black text entry background, and websites with transparency will show up as dark and unreadable.
the firefox fix above solved it for me.

---

### Post by Sand Lee on 2007-04-29
I found the [SOLUTION]...
Open Firefox
Go to Edit -> Preferences
Click on the "Content" tab
Under Fonts & Colors click Colors
Uncheck "Use system colors"
:guitar:

---

