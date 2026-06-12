---
title: "Howto launch program maximized"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by Meson on 2008-01-19
I want to create a launcher that will start the program maximized.  How do I do this?

---

### Post by kostkon on 2008-01-19
Could you be more specific? Do you have a problem with a program that does not start maximized? Which one is it?

---

### Post by Meson on 2008-01-19
No specific program.  I just want to be able to double click an icon on my desktop and have it launched maximized automatically.

---

### Post by wormser on 2008-01-19
You might want to check the man page for the program.  It might have a command line option to be maximized.  Other than that, I don't know.

---

### Post by Meson on 2008-01-19
The program is vlc... actually wxvlc... there is actually a fullscreen option that I'm using now, but maximized would be preferable.

---

### Post by kostkon on 2008-01-19
> **Meson said:**
> No specific program.  I just want to be able to double click an icon on my desktop and have it launched maximized automatically.

Right click on the Desktop, select *Create Launcher...*, browse for the program, select an icon you like and a title, and that's it, you are ready.

---

### Post by Meson on 2008-01-19
I know, but that doesn't help =)  I want it to be maximized on startup.

---

### Post by kostkon on 2008-01-19
> **Meson said:**
> I know, but that doesn't help =)  I want it to be maximized on startup.

You just confused me because you said 'no specific program'. Anyway, you can use these two command line options that set the window size:
```
--width
``` and ```
--height
```

Set the *--width* to be the value of the width of your desktop resolution, and the *--height* to be equal to the value of the height of your desktop, minus the added heights (in case you have more than one) of your panels. I think this will work.

Create a launcher that launches VLC with these parameters. Try it and post back.

---

### Post by Meson on 2008-01-19
Doesn't work for vlc.  It does work for a Firefox launcher... but that's only because height and width are specified in Firefox's man page.

---

### Post by jaytek13 on 2008-01-19
It's unfortunately a limitation of the gnome window manager. KDE 3.x window manager has a vast array of options for configuring and saving window options, such as size, position, etc... gnome is simply lacking these options by default and I'm not sure there is a particular option you could take outside of changing your window manager. 


Offhand I'm not familiar with a window manager that you could replace the default gnome manager with that would allow you to do this, but there may be one... icewm, windowmaker, afterstep, etc. Maybe someone else is here that uses these that could testify as to whether or not they support this feature.

---

### Post by chewearn on 2008-01-19
Technically, you can also set the video width and height for VLC, under Preferences > Video, when "Advanced options" is checked.

But, the results are not that good, because you cannot automatically take care of the aspect ratio (video will be cropped).

---

### Post by kellemes on 2008-01-19
[Devilspie]("https://help.ubuntu.com/community/Devilspie") is made for this.

---

### Post by roentgen on 2008-01-20
This is needed because some apps start with a few pixels off-screen and they show up on a different virtual desktop.

---

