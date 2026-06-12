---
title: "How Do You Install Themes?"
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-04-14
I know this is probably the stupidest question but i'm trying to install this theme: 
[http://www.gnome-look.org/content/show.php?content=37406](http://www.gnome-look.org/content/show.php?content=37406)
I downloaded it and extracted it to my desktop, but I'm not sure how to actually install it. Thanks in advance.

---

### Post by lazyd2 on 2006-04-14
No need to extract it. Go to System-->Preferences-->Theme and click *Install Theme*, select the theme you want and it's done...

---

### Post by twirp on 2006-04-14
[color=#FFFFFF]I believe you extract it to your .themes directory (in your home folder, it's hidden I believe you can make Nautilus show the hidden files and folders)[/color]
There are far too many helpful people...
do what lazyd2 said :p

---

### Post by therunnyman on 2006-04-14
Oops, too late.

You should try rolling your own theme someday.  It can be fun, and terrifying, and frustrating.  For an idea of how, get into a theme folder, and peruse the contents of the GTK-2.0-->gtkrfc file.

therunnyman

---

### Post by user1397 on 2006-04-14
Nevermind it worked!
Thanks guys

---

### Post by user1397 on 2006-04-14
Actually, the controls and window borders worked fine, but the icons which are supposed to look kde-ish, look like a sheet of paper. Do I have to install something for this to work? possibly some kde package?

---

### Post by twirp on 2006-04-14
[QUOTE=erik1397]Actually, the controls and window borders worked fine, but the icons which are supposed to look kde-ish, look like a sheet of paper. Do I have to install something for this to work? possibly some kde package?[/QUOTE]
Make sure everything is up-to-date.  Also, there might be problems with the theme...

---

### Post by ComplexNumber on 2006-04-14
[quote=erik1397]Actually, the controls and window borders worked fine, but the icons which are supposed to look kde-ish, look like a sheet of paper. Do I have to install something for this to work? possibly some kde package?[/quote] the reason why its doing that is because its not pointing to an icon theme. go into the GT4 theme directory and have a look at the theme.index file. it should look like this:

[Desktop Entry]
Name=GT4
Type=X-GNOME-Metatheme
Comment=Aqua style theme
Encoding=UTF-8

[X-GNOME-Metatheme]
GtkTheme=GT4
MetacityTheme=GT4


change it to look like this (the change is highlighted in bold):

[Desktop Entry]
Name=GT4
Type=X-GNOME-Metatheme
Comment=Aqua style theme
Encoding=UTF-8

[X-GNOME-Metatheme]
GtkTheme=GT4
MetacityTheme=GT4
[B]IconTheme=gnome


[/B](*note: if you don't want the icon theme to be gnome, change it to another (eg 'Tango'). but make sure that the name of the icons matches exactly the name of the icon theme in the icon directory )*

---

### Post by user1397 on 2006-04-14
Thanks guys for all the replies.

---

### Post by ComplexNumber on 2006-04-14
[quote=erik1397]Thanks guys for all the replies.[/quote] let us all know if you solve the issue and get the icons to show up :)


btw if you have trouble reading the theme.index file when you double click on it in nautilus, set the execute bits of the file to be executable, then try again. it should bring up a dialogue asking you if you want to cancel, run, open, or whatever. just open it.

---

### Post by user1397 on 2006-04-14
[quote=ComplexNumber]the reason why its doing that is because its not pointing to an icon theme. go into the GT4 theme directory and have a look at the theme.index file. it should look like this:

[Desktop Entry]
Name=GT4
Type=X-GNOME-Metatheme
Comment=Aqua style theme
Encoding=UTF-8

[X-GNOME-Metatheme]
GtkTheme=GT4
MetacityTheme=GT4


change it to look like this (the change is highlighted in bold):

[Desktop Entry]
Name=GT4
Type=X-GNOME-Metatheme
Comment=Aqua style theme
Encoding=UTF-8

[X-GNOME-Metatheme]
GtkTheme=GT4
MetacityTheme=GT4
[B]IconTheme=gnome


[/B](*note: if you don't want the icon theme to be gnome, change it to another (eg 'Tango'). but make sure that the name of the icons matches exactly the name of the icon theme in the icon directory )*[/quote]
I understand how to do this except for the  "[I]make sure that the name of the icons matches exactly the name of the icon theme in the icon directory" part.  
[/I]What does this mean? I can't find anywere an icon theme name in the icon directory!

---

### Post by ComplexNumber on 2006-04-14
> I can't find anywere an icon theme name in the icon directory! i meant the name of the directory in the icon directory.


[quote=erik1397]I understand how to do this except for the  "[I]make sure that the name of the icons matches exactly the name of the icon theme in the icon directory" part.  
[/I]What does this mean? I can't find anywere an icon theme name in the icon directory![/quote] if you look in the /usr/share/icons(or /home/<username>/.icons) directory, the gnome icons are called 'gnome'. the tango icons are called 'Tango', etc. if you specify the name of the icons that you want in the theme.index file as 'tango', it won't find the Tango icons. its case sensetive - the name of the icons that you specify in the theme.index file must match the name of the icon directory in /usr/share/icons (or /home/<username>/.icons).
the only reason why i stated "*make sure that the name of the icons matches exactly the name of the icon theme in the icon directory" *was just in case you didn't want to use the gnome icon theme.....thats all.
to make it easier, just add the line that i asked you to (ie 'IconTheme=gnome').



did all that make sense? if not, let me know and i'll rephrase it.

---

### Post by user1397 on 2006-04-15
[quote=ComplexNumber]i meant the name of the directory in the icon directory.


 if you look in the /usr/share/icons(or /home/<username>/.icons) directory, the gnome icons are called 'gnome'. the tango icons are called 'Tango', etc. if you specify the name of the icons that you want in the theme.index file as 'tango', it won't find the Tango icons. its case sensetive - the name of the icons that you specify in the theme.index file must match the name of the icon directory in /usr/share/icons (or /home/<username>/.icons).
the only reason why i stated "*make sure that the name of the icons matches exactly the name of the icon theme in the icon directory" *was just in case you didn't want to use the gnome icon theme.....thats all.
to make it easier, just add the line that i asked you to (ie 'IconTheme=gnome').



did all that make sense? if not, let me know and i'll rephrase it.[/quote]
Yes it makes sense.  I either want to make it "default.kde" or "crystalsvg", but those are the ones that don't seem to work! guess ill have to try another one...

---

### Post by user1397 on 2006-04-15
Still, thank you for your dedication and perseverance, complexnumber

---

### Post by ComplexNumber on 2006-04-15
[quote=erik1397]Yes it makes sense.  I either want to make it "default.kde" or "crystalsvg", but those are the ones that don't seem to work! guess ill have to try another one...[/quote]
not for the gnome desktop you can't. only gnome icon themes work with gnome (and gnome/gtk apps) and only kde icons work with kde (and kde/qt apps). one can port them from one to the other, but its not for the beginner to do.

---

### Post by user1397 on 2006-04-15
[quote=ComplexNumber]not for the gnome desktop you can't. only gnome icon themes work with gnome (and gnome/gtk apps) and only kde icons work with kde (and kde/qt apps). one can port them from one to the other, but its not for the beginner to do.[/quote]
Oh I see... well thank you still and I guess i'm stuck with gnome icons :)

---

### Post by ComplexNumber on 2006-04-15
[quote=erik1397]Oh I see... well thank you still and I guess i'm stuck with gnome icons :)[/quote]
so did you get your gnome icons to show up then after you added 'IconTheme=gnome' to the theme.index file?

---

### Post by user1397 on 2006-04-15
[quote=ComplexNumber]so did you get your gnome icons to show up then after you added 'IconTheme=gnome' to the theme.index file?[/quote]
Yes I did.
Sorry about not getting back to you earlier. I was busy parousing the forums...

---

