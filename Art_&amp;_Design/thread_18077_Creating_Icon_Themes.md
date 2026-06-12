---
title: "Creating Icon Themes"
date: 2005-03-04
forum: Art &amp; Design
---

### Post by cajunaggie on 2005-03-04
I trying to cobble together a custom icon theme which basically lumps the icons I like best into a theme. I've opened up the index.theme for a couple of icon sets and I've got a few questions:
1)The line that says "Inherits=gnome" means it will inherit from gnome whatever isnt't specified wiithin theme parameters?

2) The Display Depth means what precisely?

3) The "Directories" line tells Gnome what directories the theme contains. I've figured ou the different directories (128x128, 32x32, 16x16 and so forth) contain different size icons. Is it neccesary to create a different size icon for each directory or  will Gnome scale to match?

4)What the heck is the "scalable" directory for? It's been empty with just about every theme I've looked at.

---

### Post by kassetra on 2005-03-04
[QUOTE=cajunaggie]
1)The line that says "Inherits=gnome" means it will inherit from gnome whatever isnt't specified wiithin theme parameters?

2) The Display Depth means what precisely?

3) The "Directories" line tells Gnome what directories the theme contains. I've figured ou the different directories (128x128, 32x32, 16x16 and so forth) contain different size icons. Is it neccesary to create a different size icon for each directory or will Gnome scale to match?

4)What the heck is the "scalable" directory for? It's been empty with just about every theme I've looked at.[/QUOTE]

1. Yes.
2. Display Depth is normally a setting in your XF86Config or XorgConfig file...the only thing I can think of why this is in here is to specify which icon set to use for which depth, i.e. 256 color icons for low depths, high color icons for high depths... etc.
3. No, it's not necessary, especially if you're just making your own custom theme, some icons may look funny on your toolbars and such if you don't also have some 16x16 icons or so... Gnome will scale... but it may not look good.
4. scalable directories are for svg icons, that can scale to any size and look exactly the same.

---

### Post by bvc on 2005-03-04
[http://www.gnomefiles.org/app.php?soft_id=385](http://www.gnomefiles.org/app.php?soft_id=385)

---

### Post by kassetra on 2005-03-04
[QUOTE=bvc][http://www.gnomefiles.org/app.php?soft_id=385]("http://www.gnomefiles.org/app.php?soft_id=385")[/QUOTE]

That's a great little program.  :)  I really think it's a good utility.

---

### Post by cajunaggie on 2005-03-04
For some reason the package can't download from the site. Are there any other sources?

---

### Post by bvc on 2005-03-04
[http://forge.novell.com/modules/xfmod/project/?gib](http://forge.novell.com/modules/xfmod/project/?gib)

---

