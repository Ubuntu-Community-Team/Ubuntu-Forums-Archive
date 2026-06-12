---
title: "Adding Icon for .mdf in Gnome"
date: 2007-10-13
forum: Art &amp; Design
---

### Post by arsenic23 on 2007-10-13
Ok, so this week I decided to take a look at how Gnome handles its icon themes, and make myself a small theme that inherits from and addresses some of my dislikes of Ubuntu's Human theme.

ANYWAY, everythings been going smoothly up until tonight.  What I want to do is take the icon I made for .iso files and share it with similar filetypes, namely .mdf files.  Now I was hoping that I could just link mdf.png(svg) to my application-x-cd-image.png(svg) file.  Nope.  So after looking through a fair bit of other themes and poking my nose about I can't figure out for the life of me how to get .mdf files to have an icon.

So how do I set up icons for file formats that Gnome doesn't normally carry icons for ??

---

### Post by Hairy_Palms on 2007-10-13
i assume it gives them the standard binary file icon? well if gnome doesnt recognise it as a cd image then it wont give it a CD image icon, theres no way around it afaik, though you can give individual files custom icons.

---

### Post by arsenic23 on 2007-10-13
Ok !  I figured it out.  Here's how to add a new mime type in Gnome for anyone else who wants to know.

Go to the main mime dir and create a new mimefile for your filetype ( I'm doing .mdf here ):
```
cd /usr/share/mime/packages
gksudo gedit [COLOR="#8b0000"]mdf[/COLOR].xml 
```

Paste the following into your text editor window and save it:
```
<?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
    <mime-type type="application/[COLOR="DarkRed"]x-cd-image[/COLOR]">
        <comment>[COLOR="DarkRed"]MDF[/COLOR]</comment>
        <glob pattern="*[COLOR="DarkRed"].mdf[/COLOR]"/>
  </mime-type>
</mime-info>
```

Now just update your mime database with this command :
```
update-mime-database ..
```

Note that the *"application/x-cd-image"* part makes the correct icon file the ./mimetypes/application-x-cd-image.svg(png) in your icon theme directory.   Simply change the red parts and you can add any mimetype you wish.

---

### Post by Hairy_Palms on 2007-10-13
well you learn something everyday :) thats good to know thanks arsenic

---

### Post by cong06 on 2010-10-04
> **arsenic23 said:**
> Ok !  I figured it out.  Here's how to add a new mime type in Gnome for anyone else who wants to know.

Go to the main mime dir and create a new mimefile for your filetype ( I'm doing .mdf here ):
```
cd /usr/share/mime/packages
gksudo gedit [COLOR="#8b0000"]mdf[/COLOR].xml 
```

Paste the following into your text editor window and save it:
```
<?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
    <mime-type type="application/[COLOR="DarkRed"]x-cd-image[/COLOR]">
        <comment>[COLOR="DarkRed"]MDF[/COLOR]</comment>
        <glob pattern="*[COLOR="DarkRed"].mdf[/COLOR]"/>
  </mime-type>
</mime-info>
```

Now just update your mime database with this command :
```
update-mime-database ..
```

Note that the *"application/x-cd-image"* part makes the correct icon file the ./mimetypes/application-x-cd-image.svg(png) in your icon theme directory.   Simply change the red parts and you can add any mimetype you wish.

I can see this being very useful, but haven't gotten it to work quite yet.

I have 3 types of files: z64, v64, and n64. n64 is already recognized by nautilus (it's labeled as "Nintendo Roms (application/x-n64-rom)")
I've figured out how to put icons on n64 file extensions. (~/.icons/ etc.)

Now I want to include the other two. Since it's so much cleaner to just use the same mime-type, I tried this:

```

isaac@bohr:/usr/share/mime/packages$ cat z64.xml 
<?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
    <mime-type type="application/x-n64-rom">
        <comment>Nintendo Roms</comment>
        <glob pattern="*.z64"/>
  </mime-type>
</mime-info>
isaac@bohr:/usr/share/mime/packages$ sudo update-mime-database ..

```

But *.z64 files still show up as:
z64 document (application/x-extension-z64)

Which I suspect is the default "We have no idea what this file extension is"
Note: I've also tried to just do file icons the "obvious way" but "~/.icons/gnome/32x32/mimetypes/gnome-mime-application-x-extension-z64.png" doesn't work. Anyway, this isn't as clean as doing it at mimetypes.

---

