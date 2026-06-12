---
title: "Adding truetype fonts to /usr/share/fonts/truetype"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by ltk5 on 2007-02-16
I'm trying to add some windows fonts to my /usr/share/fonts/truetype. But I can't copy them. Now, I guess there's another way of doing it, which I'm not aware of.
I'm using Ubuntu Edgy

---

### Post by shareMenaPeace on 2007-02-16
How did you tried to copy the file?

you can use admin privileges to copy to certain protected folders, with sudo.

example how to change the ubuntu usplash from lafter login.

```
cd /usr/share/pixmaps/splash
sudo ln -sf mysplash.png ubuntu-splash.png
sudo cp /home/username/mysplash.png /usr/share/pixmaps/splash
```

---

### Post by ltk5 on 2007-02-16
i tried copying it with sudo
```
sudo cp /home/lotko/download/net/my_fonts /usr/share/fonts/truetype
```

but it says, that the file doesn't exist (or something like that). so I copied the exact location into the terminal and it still didn't want to copy. I've read that KDE has a program for installing fonts, what about GNOME?

thanks!

---

### Post by konst88 on 2007-02-16
sudo cp /home/lotko/download/net/my_fonts**/*** /usr/share/fonts/truetype

---

### Post by kerry_s on 2007-02-16
Just create a folder in your home named .fonts and drop all your fonts in there.

---

### Post by ltk5 on 2007-02-16
> **konst88 said:**
> sudo cp /home/lotko/download/net/my_fonts**/*** /usr/share/fonts/truetype
oh, so it's the asterisk I forgot about! I'll try that :) 


> **kerry_s said:**
> Just create a folder in your home named .fonts and drop all your fonts in there.
is there any difference between the /usr/share.. and the /home folder for fonts. Can all programs, get them from the /home or just some?

---

### Post by Icebear on 2007-02-16
In Synaptic do a search for msttcorefonts.

This pakages downloads the following M$ Fonts
 
Andale Mono
  Arial Black
  Arial (Bold, Italic, Bold Italic)
  Comic Sans MS (Bold)
  Courier New (Bold, Italic, Bold Italic)
  Georgia (Bold, Italic, Bold Italic)
  Impact
  Times New Roman (Bold, Italic, Bold Italic)
  Trebuchet (Bold, Italic, Bold Italic)
  Verdana (Bold, Italic, Bold Italic)
  Webdings

---

### Post by ltk5 on 2007-02-16
I know about msfonts. But I don't want them, ever. The problem is because I found some cute fonts on the web, which aren't the default windows ones.
I'll try moving them to .fonts/ and rebooting the system.
thanks everyone:KS

---

### Post by geovino on 2007-03-08
> **kerry_s said:**
> Just create a folder in your home named .fonts and drop all your fonts in there.


That worked well! I created the .font folder in the home/davek folder and added one font. Then is disappeared! but I then opened OpenOffice drawing and the font had been added! So if I want to add another font or fonts I have to create a new .font folder every time?

---

### Post by Bachstelze on 2007-03-08
[https://help.ubuntu.com/community/FontInstallHowto](https://help.ubuntu.com/community/FontInstallHowto)

Actually, this isn't very clear... In KDE, we have a module in KControl to add fonts :

[[IMG]http://img259.imageshack.us/img259/765/kdefontbm4.th.png[/IMG]](http://img259.imageshack.us/img259/765/kdefontbm4.png)

Isn't there something similar in the Gnome control centre ?

---

