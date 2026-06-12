---
title: "Changin desktop background from the command line"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by franestepona on 2007-01-25
Hi all!! I was wondering if it was possible to change desktop background directly from the command line. I dont want to install a fancy background switcher, just one command to a simple change. Is that possible? I couldnt find any information for that, and looks pretty basic option... 

Someone knows???

Thanks

---

### Post by franestepona on 2007-01-25
Just something like 
```
gnome-background-change --set mybackground.jpg
```

---

### Post by hyper_ch on 2007-01-25
What GUI are you using?

---

### Post by franestepona on 2007-01-25
> **sjau said:**
> What GUI are you using?

I dont really understand what u mean. I normally do it trough Desktop preferences (right click in the desktop). Well the thing is that i want to make a shell script to change Desktop background, GTK2 theme and emerald theme. Let's say one to make all them brownish, greenish, etc. in just one click. Maybe there is already a program for it, but i couldnt find anything :(

---

### Post by ashkendo on 2007-01-25
> **franestepona said:**
> I dont really understand what u mean.

I think he is asking what Desktop Environment or Window Mananger you are using.  That will make a difference as to what the command will be.

---

### Post by ardchoille42 on 2007-01-25
To set the background from the command line:
```

gconftool-2 --type string --set /desktop/gnome/background/picture_filename "/path/to/image.ext"

```

To set the gnome splash screen from the command line:
```

gconftool-2 --type string --set /apps/gnome-session/options/splash_image "/path/to/image.ext"

```

If you open gconf-editor and go to /apps/gnome-session/options/splash_image you'll see the setting for it. The setting path in the command line is the same as in gconf-editor (ie, /apps/gnome-session/options/splash_image). I use this method i a master script (to run just after a fresh install) to set things because it's faster to do it in command line rather than opening gconf-editor and browsing to and changing settings.

You can use gconftool-2 for a lot of things:

```

man gconftool-2

```

---

### Post by franestepona on 2007-01-25
Thank you! you are the man!

---

