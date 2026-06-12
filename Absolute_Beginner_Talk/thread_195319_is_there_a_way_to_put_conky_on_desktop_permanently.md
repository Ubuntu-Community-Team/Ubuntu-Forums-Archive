---
title: "is there a way to put conky on desktop permanently?"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by maddbaron on 2006-06-12
is there a way to make conky a permanent feature on the desktop so it can show up all the time?

---

### Post by taurus on 2006-06-12
Assuming you are using Gnome, click System -> Preferences -> Sessions -> Startup Programs.  Click Add and type in "conky" and click Okay.  Log out and back in again and conky will be on your desktop!!!

---

### Post by maddbaron on 2006-06-12
nope. it started it up then promptly went away..

n e more ideas?

---

### Post by MatthiasMatthias on 2006-06-12
What is conky?

---

### Post by taurus on 2006-06-12
[QUOTE=maddbaron]nope. it started it up then promptly went away..

n e more ideas?[/QUOTE]
The problem is that you try to run conky with nautilus!!!  Read #3 from this link, [http://conky.sourceforge.net/faq.html](http://conky.sourceforge.net/faq.html)...

---

### Post by maddbaron on 2006-06-12
so how can i do either one of these two?

> #
Q: Conky won't stop flickering

A: Conky is designed to draw to the root desktop window. However, there are several other applications which like drawing to the root desktop window. Because of this, Conky has two options available to get around this problem:

    * You can try enabling double-buffer. Conky's double-buffer option uses the X double-buffer extension to provide a flicker-free Conky.
    * Conky can run in windowed mode, meaning that instead of drawing the the root window it draws to it's own window. You can move this window around and resize it by right-clicking or left-clicking on the window while holding down the Alt key.

---

### Post by taurus on 2006-06-12
You need to edit your ~/.conkyrc and enable the double-buffer thing!
```

double_buffer yes

```

---

### Post by bluevoodoo1 on 2006-06-12
And you may have to add the "dbe" module to your xorg.conf (I had to)....

[http://ubuntuforums.org/showpost.php?p=579902&postcount=90](http://ubuntuforums.org/showpost.php?p=579902&postcount=90)

---

### Post by maddbaron on 2006-06-12
how do i do that? how do i access the ~/.conkyrc file i need to edit please?

---

### Post by maddbaron on 2006-06-13
bump

---

### Post by taurus on 2006-06-13
```

gedit ~/.conkyrc

```
And if you don't one, then head over to [http://conky.sourceforge.net/screenshots.html](http://conky.sourceforge.net/screenshots.html) and download whichever screeshot that you like best.  Save it as .conkyrc in your home directory, ~/.conkyrc.  Then use it and modify by adding or removing things that you like or don't like...

p.s.  Please stop the bump thing because I hate that!!!  :-$

---

### Post by u-blunt-2 on 2006-06-17
I have tried both (double buffer and windowed mode). Windowed mode is quite unsexy (migh as well just start gnome-system-monitor) and enabling double buffer still doesn't keep the icons on my desktop from disappearing whenever conky refreshes.

Does anyone know how to fix this ???

---

### Post by 5-HT on 2006-06-17
[quote=u-blunt-2]I have tried both (double buffer and windowed mode). Windowed mode is quite unsexy (migh as well just start gnome-system-monitor) and enabling double buffer still doesn't keep the icons on my desktop from disappearing whenever conky refreshes.

Does anyone know how to fix this ???[/quote] 
The version of Conky in the repos is a little outdated.
Newer versions include more option support allowing conky to run in its own borderless (undecorated) window. :p

My advice would be to compile conky from source following the walkthrough in this guide: [http://ubuntuforums.org/showthread.php?t=139262]("http://ubuntuforums.org/showthread.php?t=139262")

I run conky in Gnome with its own window with double-buffer support to eliminate flickering.
If you want to run conky in Gnome with Nautilus drawing the desktop, you will need to have conky use its own window (double buffer just helps reduce flickering).

If you add the following options to your ~/.conkyrc, you won't even notice that Conky is being run in its own window (you will need to either set up transparency or use the same colour in the window as your desktop if you want the window to blend in completely with the rest of the desktop).

```
own_window yes
own_window_type normal
own_window_hints below sticky undecorated
double_buffer yes 
``` 


Conky's sample config file is well documented, and most of the options shown above are noted in there - some just haven't been activated by default.

In addition, Conky's man page is *very* well documented and describes *all* config options.

Hope that helps.

---

### Post by u-blunt-2 on 2006-06-19
Wow... after 2 weeks of messing around with conky, GOD BLESS YOU !

---

### Post by Beej on 2006-06-19
2 ways to do it

1.from terminal

"sudo gedit ~/.conkyrc"

~/ is a short way of typing /home/myusername, files that are hidden in nautilus start with a .

2.Through nautilus

go to your home folder in nautilus press ctrl+h (or go to view > show hidden files)

you should then be able to find the file. Right click on it, open with text editor will also do the job.

hope this helps,

Beej.

---

