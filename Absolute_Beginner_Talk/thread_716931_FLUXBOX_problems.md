---
title: "FLUXBOX problems"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by boboyo2 on 2008-03-06
hi
ive had fluxbox for maybe 2 months and i still cant find a way to change the letters because they are too small

---

### Post by saj0577 on 2008-03-06
What letters?
Please be more specific.

Saj

---

### Post by herbster on 2008-03-06
Yes, please be more specific, hehe. That's far too vague.

Might you be talking about the font size of your menu and/or your toolbar?

---

### Post by boboyo2 on 2008-03-06
its the font 

u know when i right-click and the menu thing

and also the fonts in firefox

---

### Post by kerry_s on 2008-03-06
you can 
1. change the font size in the theme
2. change the dpi with ~/.Xdefaults
Xft.dpi: 75 <- mine's set low for small fonts. you want higher than 96 for larger fonts.
Xft.antialias: true
xft.hinting: true
xft.rgba: rgb

3. change the font size with ~/.gtkrc-2.0
gtk-font-name = "sans 12"

4. read the manual
[http://fluxbox.sourceforge.net/docbook/en/html/](http://fluxbox.sourceforge.net/docbook/en/html/)

---

### Post by boboyo2 on 2008-03-06
how do i change the dpi?

---

### Post by herbster on 2008-03-06
Yep, go to ~/.fluxbox/styles/yourtheme/theme.cfg. Look for the Font section, typically at the very bottom, and you can change it there. Just be sure you use Font Name-10, the name is attached with a dash to the size.

To change DPI, open your ~/.Xdefaults file. If you don't have one, it's all the same.

```
gedit ~/.Xdefaults
```

Then paste what kerry_s has shown, adjusting to your preference. Mine are:

```
!Xft settings
Xft.dpi:                96
Xft.hinting:            1
Xft.hintstyle:          hintfull
Xft.antialias:          1
Xft.rgba:               rgb
```

---

### Post by boboyo2 on 2008-03-06
i dont rly know how to use flux and i dont know howto find ~/.fluxbox/styles/yourtheme/theme.cfg

---

### Post by herbster on 2008-03-06
Ah, no sweat. Use the flux menu and go to Styles and see which theme you are using, what the name is. Then in terminal:

```
cd .fluxbox/styles/nameoftheme
```

Whatever theme you are using, replace "nameoftheme" with it, of course remember to keeps the case the same-- ie., if your theme is Fawn, you would do

```
cd .fluxbox/styles/Fawn
```

Now:

```
gedit theme.cfg
```

Look for a line similar to this:

```
*font:   			Arial-9
```

Change the Arial to the font you want and the 9 to the size you want. You just have to change them, hit Save in gedit and then bring up your flux menu and hit Reconfigure. This will show the new font instantly, so you can just keep changing the font in the editor and saving until you find one you like.

---

### Post by eriqjaffe on 2008-03-06
> **herbster said:**
> ```
gedit theme.cfg
```If you don't have gedit, use whatever text editor you use.  If you're not sure, you can just use Nano, which will let you edit the file right in the terminal.

---

### Post by quequeque on 2008-03-07
when i get to the gedit.cfg part thers a new window but theres nothing written on it

btw cd .fluxbox/styles/nameoftheme didnt work for me 
i had to write cd home/nameofuser/.fluxbox/styles/nameoftheme

---

### Post by quequeque on 2008-03-07
when i get to the gedit.cfg part thers a new window but theres nothing written on it

btw cd .fluxbox/styles/nameoftheme didnt work for me
i had to write cd /home/nameofuser/.fluxbox/styles/nameoftheme

---

### Post by herbster on 2008-03-07
quequeque, Hmm, you were probably using a terminal that had been cd'd to another directory then. Open a terminal and

```
cd .fluxbox/styles
ls
```

You get a list of the directories, which are the flux styles you have. Then, just

```
cd nameofwhichevertheme && gedit theme.cfg
```

Gedit should open up with the theme.cfg, which you can now edit. It's not gedit.cfg, it's "gedit theme.cfg" as gedit = the program, the text editor itself; "theme.cfg" = the flux theme configuration file.

---

### Post by quequeque2 on 2008-03-07
what do i write in terminal for nano?

---

### Post by herbster on 2008-03-07
Just replace "gedit" with "nano".

---

### Post by quequeque2 on 2008-03-08
thank you
i will try it :)
and do you know how to change the flux background?

---

### Post by quequeque2 on 2008-03-09
i didnt use nano or gedit, i used notepad using wine

now, its all ok but when i start firefox, its still the old small letters

---

