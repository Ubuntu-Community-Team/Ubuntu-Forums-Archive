---
title: "install fonts for openoffice"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by ikilledclown on 2006-06-16
How do you install a font for openoffice?
I tried the howto on the forums but it doesnt work because it asks me to install a font from usr>share>fonts>truetype but everytime I try to put the ttf file in to that folder and it said i didnt have the persmission to paste this file here.

How can I install a font?

Cheers

---

### Post by simone.brunozzi on 2006-06-16
Well,
fonts are not openoffice-specific, but general for the computer you use.

Try to install **msttcorefonts** with Synaptic (Ubuntu) or Adept (Kubuntu), probably the font you're looking for is there.

Cheers,

---

### Post by bruce89 on 2006-06-16
There is a local font directory - go to nautilus and press Control+L, and then put in ```
fonts:///
``` you can then add fonts here.

---

### Post by ikilledclown on 2006-06-16
where do I find nautilus?
Probably obvious but thats me!!

---

### Post by bruce89 on 2006-06-16
[QUOTE=ikilledclown]where do I find nautilus?
Probably obvious but thats me!![/QUOTE]
It's the file browser, so Places>Home Folder will open it.

---

### Post by Jagot on 2006-06-16
The only directory you can write to by default is your /home directory.

To add fonts to /usr/share/fonts/truetype you can do it two ways - the graphical or the command line.

Graphical first:

Hit alt+f2 then type:

```
gksudo nautilus
```

This opens the file browser as root, which essentially means you can drag and drop files anywhere.  So, you should now be able to drag and drop your fonts to that directory.

Second way is command line:

Place the fonts or the directory containing your fonts on the desktop.  Now open a terminal and type the following:

```
sudo mv ~/Desktop/My\ Fonts /usr/share/fonts/truetype/
```

This will move the directory called My Fonts which is on the desktop to the /usr/share/fonts/truetype directory.

Now, with either the graphical method or the command line, this will not do on it's own - you need to make Ubuntu recognise the fonts, so in terminal you need to type:

```
sudo fc-cache -f -v
```

The methods above make the fonts system wide.  If you just want them to be available to you, the you could just create a directory in your /home called '.fonts' and put the fonts you want in there then run sudo fc-cache -f -v to get Ubuntu to recognise them.

---

### Post by bruce89 on 2006-06-16
fonts:/// opens ~/.fonts, which you can add fonts to as it is the home folder.

---

