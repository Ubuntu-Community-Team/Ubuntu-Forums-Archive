---
title: "Fonts"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by richard978 on 2008-03-28
I'm really stuck on Fonts. I've recently moved from windows and I've purchased about £900.00 worth of post script fonts so I want to use them with Ubuntu.

Firstly is there an easy way to add them and secondly how the hell do you manage large numbers of fonts in Ubuntu. Is there a font manager that works?

---

### Post by Inxsible on 2008-03-28
Hate to break it to you, but not all fonts(made for Windows) will work in Linux. You can try however and see if they work. 

If you have the option of requesting the Linux fonts from where ever you bought them, that could be another solution.

---

### Post by richard978 on 2008-03-28
Is there any software available to manage and install fonts other than command line

---

### Post by mali2297 on 2008-03-28
A quick search gave me this:
[http://fontmatrix.net/](http://fontmatrix.net/)

It might be worth to try?

---

### Post by richard978 on 2008-03-28
Ok cheers, there's a bunch of file and no deb format. I've downloaded the source file now I'm completely lost what next?

---

### Post by SunnyRabbiera on 2008-03-28
well if they are ttf they might work, i have no issue using microsoft true type fonts.
if they are another kind of font it might not work though

---

### Post by justsomedude on 2008-03-28
[http://www.pcbypaul.com/software/FONTpage.html](http://www.pcbypaul.com/software/FONTpage.html)

[http://uwstopia.nl/blog/2007/06/gnome-specimen-0-2-is-out](http://uwstopia.nl/blog/2007/06/gnome-specimen-0-2-is-out)

or gwaterfall (available in Universe)

If you just want to install a font as a user:


1. Create a folder named .fonts in your home directory (notice the dot at the beginning).

2. Unpack your fonts there.

3. Restart X: Press [Ctrl] + [Alt] + [Backspace]

4. In terminal:

```
sudo fc-cache
```

Sorry for the terminal usage, you can do it. ;)

5. Configuration (Optional):

```
sudo dpkg-reconfigure fontconfig-config
```

and then

```
sudo dpkg-reconfigure fontconfig
```

..and restart X again.

6. Done.


Font preferences can be accessed under System --> Preferences --> Appearance --> Fonts

---

### Post by mali2297 on 2008-03-28
> **richard978 said:**
> Ok cheers, there's a bunch of file and no deb format. I've downloaded the source file now I'm completely lost what next?

Another link:
[http://phorolinux.com/manage-fonts-with-fontmatrix.html](http://phorolinux.com/manage-fonts-with-fontmatrix.html)

---

### Post by richard978 on 2008-03-28
I'm going for it....wish me luck

---

### Post by penguindev on 2008-04-01
Hey richard, you should just be able to drag windows .ttf fonts into your ~/.fonts directory, and restart apps or some apps like gimp can refresh font lists just by clicking a button.

By the way, you could try this:
[http://fontmanager.blogspot.com](http://fontmanager.blogspot.com) and see if it helps you out at all, if you have a lot of fonts and things get cluttered.

---

