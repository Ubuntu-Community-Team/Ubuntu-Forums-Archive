---
title: "How do you install themes?"
date: 2007-01-14
forum: Art &amp; Design
---

### Post by mattmagician on 2007-01-14
its tar.gz
and if i extract, it says file type invalid, if i dont, file type invalid.

any help?

---

### Post by ButteBlues on 2007-01-14
For GTK and Metacity themes, untar to: ~/.themes

For icon themes, untar to: ~/.icons

Then it should appear in the theme manager.

---

### Post by mattmagician on 2007-01-14
ok, because i'm a newb, i dunno what your talking about. lol.
can you walk me through it a little? its this one.

---

### Post by ButteBlues on 2007-01-14
> **mattmagician said:**
> ok, because i'm a newb, i dunno what your talking about. lol.
can you walk me through it a little? its this one.
Okay - download the file and double click it.

Choose "Extract".

In your home folder, right click and choose "Show Hidden Files".

Open a folder named ".themes"

Extract all files to that folder.

Open the main menu - System > Preferences > Theme.

Click the "Customize button".

In the first tab, choose Vista Black.

Close and exit.

---

### Post by mattmagician on 2007-01-14
how cann i extract to that folder? its not showing in the tree.

---

### Post by mattmagician on 2007-01-14
correction, its not in the Theme box.

---

### Post by paparucino on 2007-01-15
> **mattmagician said:**
> correction, its not in the Theme box.
If you only want to install the theme, you must look for an icon called Theme in System-> Preferences or in in System -> Control Center, this depends by the version and the update of Ubuntu.
Click on Theme -> Install Theme, look for Black Vista.tar.gz and click on it.
That's all folk.
If you want to modify or see the structure of that theme, open a terminal (gmome-terminal) then goto to the folder/directory where your file is then type:
```

tar -zxvf black Vista.tar.gz

```
And voilà, the file is ready for your job

---

### Post by Circus-Killer on 2007-01-15
> **paparucino said:**
> If you only want to install the theme, you must look for an icon called Theme in System-> Preferences or in in System -> Control Center, this depends by the version and the update of Ubuntu.
Click on Theme -> Install Theme, look for Black Vista.tar.gz and click on it.
That's all folk.
If you want to modify or see the structure of that theme, open a terminal (gmome-terminal) then goto to the folder/directory where your file is then type:
```

tar -zxvf black Vista.tar.gz

```
And voilà, the file is ready for your job

exactly as paparucino said, except i have one thing to add.

if you are running edgy, you may need to install gtk2-engines-pixbuf (dont know why its not installed by default)

---

### Post by mattmagician on 2007-01-15
OK, since i tried that,and it looked like it would work i'll show you what poped up.
Picture is attached.

---

### Post by paparucino on 2007-01-15
> **mattmagician said:**
> OK, since i tried that,and it looked like it would work i'll show you what poped up.
Picture is attached.
It means that the file you downloaded has a not valid format for Gnome.
Where did you get it?

in the meanwhile give a glance at these sites
[http://art.gnome.org/backgrounds/other/](http://art.gnome.org/backgrounds/other/)
[http://gnome-look.org/](http://gnome-look.org/)
may be you'll find something interesting for you

---

### Post by ComplexNumber on 2007-01-15
**mattmagician**
its not a valid theme. theres nothing you can do about installing it.


btw for future reference, don't bother installing themes via the theme manager because it has a limitation(ie it can't handle zipped up files that contain more than 1 file). just right click on the tarball(ie files that have tar,gz or tar.bzip2, etc) and place in /home/<your-username>/.themes.

---

### Post by mattmagician on 2007-01-15
someone on here had it. its a tar.gz file..

---

### Post by ComplexNumber on 2007-01-15
> **mattmagician said:**
> someone on here had it. its a tar.gz file..
there's nothing wrong with the file format. whats wrong is that its not a theme. here are 2 screenshots - the 1st one that show you the contents of black vista.tar.gz(that you gave in post 3 in this thread), and the 2nd one is the contents of what a theme should look like (after unzipping the file and opening the theme directory).
there should be at least one of gtk-2.0 or metacity-1 directories for it to be a valid theme. when i opened up the pixmap directory in the vista black that you'd given, there was no sign of a gtkrc.

the file that you've given is not a theme for gnome because its neither a metacity theme, emerald theme, compiz theme, icon theme, or gtk theme.

---

### Post by paparucino on 2007-01-15
[QUOTE=ComplexNumber;2016961ì
the file that you've given is not a theme for gnome because its neither a metacity theme, emerald theme, compiz theme, icon theme, or gtk theme.[/QUOTE]
It's a theme valid for fluxbox or other *box. The structure of theme.cfg is the one for those window manager.

---

### Post by mattmagician on 2007-01-16
> in the meanwhile give a glance at these sites
[http://art.gnome.org/backgrounds/other/](http://art.gnome.org/backgrounds/other/)
[http://gnome-look.org/](http://gnome-look.org/)
may be you'll find something interesting for you

How do i install the ones on Gnome-look?

---

### Post by paparucino on 2007-01-16
> **mattmagician said:**
> How do i install the ones on Gnome-look?
The procedure is different depending on what you want to install. For wallpapers, e.g. you download the image then right click on the desktop ->Change desktop background -> Add wallpaper then goto the folder/directory where your downloaded image is.
For other features it's a little more complex, if you need, ask for help :-)

---

### Post by mattmagician on 2007-01-16
i'm trying to install themes, lol.

---

### Post by doerum on 2007-01-17
Hi

for more themes and misc. Check out [www.gnome-look.org](www.gnome-look.org) (or was it .com). There you'll find several themes and good stuff. Last time i was there, i did also find instructions for installing the themes.

---

### Post by bvc on 2007-01-17
[http://art.gnome.org/faq.php](http://art.gnome.org/faq.php)

---

