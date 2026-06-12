---
title: "Where &amp; How To Save Downloaded Wallpaper"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by LaDeDa on 2007-11-18
I downloaded a wallpaper I want to use as a desktop background in KDE.  Where do I save the picture to ensure it's invoked each boot ?? T
IA

---

### Post by Paul820 on 2007-11-18
Just make a folder called wallpapers in your home folder, go to your wallpaper settings and browse to the wallpaper you want. It will get read from that folder at bootup.

---

### Post by LaDeDa on 2007-11-18
Naw, there's already some folder with several wallpapers in it.  Right click anywhere on the desktop and choose "configure desktop".  There is a list of around fifteen backgrounds.
How do I get my picture into the same folder ??

---

### Post by wydra on 2007-11-18
What distro of Ubuntu are you running?

In 6.06 there is an add wallpaper button.

---

### Post by LaDeDa on 2007-11-18
Kde 7.10

---

### Post by jordanmthomas on 2007-11-18
Well, the wallpapers for kde are saved in /usr/share/kde/wallpapers
(I think...in arch it's in /opt/kde/...)

This isn't writable by you, though, so you'll want to either 
```
sudo chown -r $USER /usr/share/kde/wallpapers
```
or just have your own wallpaper like sane people.

---

### Post by LaDeDa on 2007-11-18
I've got the photo sitting on the desktop , and after KDE loads, I click and use the photo as background.  Thought it might be better to have the photo listed and be able to permantly set it as background.

---

### Post by jordanmthomas on 2007-11-18
Well, here's what most people do:
make a folder somewhere for saving wallpaper and put picture in it.

right click on your dekstop and go to configure desktop.
Then, drag your picture onto the little monitor picture in the window that comes up.

Your wallpaper will stay set until you change it to something else.

---

### Post by Paul820 on 2007-11-18
> **jordanmthomas said:**
> Well, here's what most people do:
make a folder somewhere for saving wallpaper and put picture in it.

right click on your dekstop and go to configure desktop.
Then, drag your picture onto the little monitor picture in the window that comes up.

Your wallpaper will stay set until you change it to something else.

That's what i said to do, it's what everyone does. I don't know why the op thinks it won't be permanent.:confused:

---

### Post by LaDeDa on 2007-11-18
Got it.  Thank you both.

---

