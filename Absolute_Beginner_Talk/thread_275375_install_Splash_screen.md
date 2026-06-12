---
title: "install Splash screen"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by Bahal on 2006-10-11
Hi
Im tring to install screen splash, downloaded from look.gnome.com.

How do I do it?:
  system>login window> add...
I have even made a folder in /home/name  for splash-files.

Those files that I have downloaded have different formats. png and xpm are to examples. When I try to install it, I get this error: 
   "File not a tar.gz or tar archive"

I used Archive Manager to make the files to tar.gz. But still I get error...

pleas help me
(*,)
thx]

---

### Post by kevinlyfellow on 2006-10-11
could you link to the image you want to use as a splash screen?

---

### Post by Bahal on 2006-10-11
here you go:
[http://www.gnome-look.org/content/show.php?content=24581](http://www.gnome-look.org/content/show.php?content=24581)

---

### Post by AcesAndEights on 2006-10-11
You're trying to install a splash screen as your login screen. They are in different formats, so its not going to work. If you want that as your splash screen you need to install the splash screen manager. Which you can do with 

```
sudo apt-get install gnome-splashscreen-manager
```

After you do that, go System>Preferences>Splash Screen. Click 'Install', find your image and the 'Activate'. I hope that helps.

---

### Post by kevinlyfellow on 2006-10-12
Or if you don't like command line, you can always open up synaptic package manager (under the system -> preferences menu) and search for "gnome-splashscreen-manager".

---

### Post by NewRubberSoul on 2006-10-12
So that would change the brown box that pops up right after you log in?  The one that says "loading nautilus", etc?  Or would that utility just change the log in screen?

---

### Post by jordanmthomas on 2006-10-12
That would be the brown box you're talking about.

---

