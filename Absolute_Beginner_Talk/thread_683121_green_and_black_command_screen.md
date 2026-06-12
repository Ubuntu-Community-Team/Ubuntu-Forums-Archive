---
title: "green and black command screen"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by EddySanders on 2008-01-30
I'm a new user of Ubuntu, but i enjoy working with commands and terminals... i also like the green letters on black BG... 

What i want to know is, step by step, how to configure my computer to not boot the GUI, but instead take me to a shell command line.. i also would like that screen to follow the Green on Black BG color scheme..

Thanks

---

### Post by jan quark on 2008-01-30
when ubuntu starts there is the grub loader

and one option is booting into recovery mode, this should bring you to a text based system

---

### Post by EddySanders on 2008-01-30
ok. how can i configure the grub screen to be green and black?

Those colors are easier on my eyes :)

---

### Post by spiderbatdad on 2008-01-30
when you open the terminal, you can select Edit>>Edit Current Profile. Navigate to Colors and uncheck the use system colors box. Then you can select a built-in scheme or make your own by selecting the text and background box in turn, and editing the color. Just use mouse to spin the color wheel, then move circle to desired shade...how awesome!

---

### Post by Scarath on 2008-01-30
> **spiderbatdad said:**
> when you open the terminal, you can select Edit>>Edit Current Profile. Navigate to Colors and uncheck the use system colors box. Then you can select a built-in scheme or make your own by selecting the text and background box in turn, and editing the color. Just use mouse to spin the color wheel, then move circle to desired shade...how awesome!

I think the OP'er means, how do u get green text when X isnt running, not in the terminal emulators that run on the desktop. 
Am i correct? 

I would also like to know this as it would look very cool.

EDIT: found some links that may help

[URL="http://www.linuxquestions.org/questions/linux-general-1/how-change-text-color-using-linux-in-text-mode-only-runlevel-3-163814/"]
Link 1[/URL]
[Link 2]("http://www.linuxforums.org/forum/linux-desktop-x-windows/2647-change-text-color-console-terminal.html")

---

### Post by EddySanders on 2008-01-30
yes i would like the GUI not to be running and upon booting go directly to command line... not terminal emulators

also: would someone please put step by step instructions on how to change the colors? and how to set the console as my default bootup option

---

### Post by jordanmthomas on 2008-01-30
```
sudo update-rc.d -f gdm remove
```
will make gdm not start at boot.

This should work for your terminals to have green text:
```
for I in 1 2 3 4 5 6; do setterm -background black -foreground green -store > /dev/tty$I; done
```
You can put this in /etc/rc.local and tty1-tty6 will now have a green foreground after you boot up.

Or to just do one at a time:
```
setterm -background black -foreground green -store
```

---

### Post by EddySanders on 2008-01-30
one last thing... will this still show my grub screen? because i dual- boot vista

---

### Post by jordanmthomas on 2008-01-30
Yes, everything will be the same except that instead of the brown gdm screen, you'll be greeted with a terminal login (that's green) and to start an Xsession you'll either need to 
```
sudo /etc/init.d/gdm start
```
or fix yourself up an .xinitrc and use startx to run your X session.

---

### Post by EddySanders on 2008-01-30
how do i do the second thing? :)

also thanks to you all.. i never got this support with windows :D

---

### Post by jordanmthomas on 2008-01-30
```
nano .xinitrc
```
put this in there:
```
#!/bin/sh
# ~/.xinitrc
# Executed by startx (run your window manager from here)

# put things you want to run here, if they need to stay running, be sure to put an & at the end

#now, start your window manager / desktop session
exec gnome-session

```

Now, if you run startx, gnome will start and if you log out of gnome, you'll return to your terminal.  Obviously, this is a simple .xinitrc.  Here's mine:
```
#!/bin/sh
xmodmap ~/.Xmodmap
xbindkeys
gnome-volume-manager &
awesome-monitor &
xcompmgr -cC &
feh --bg-scale "/home/jordan/wallpaper/Archer DeepBlack.png"
exec awesome

```
so you can kind of get the idea, right?

---

### Post by EddySanders on 2008-01-30
you guys are awesome.. im rebooting now, and ill let you know how it worked out.

---

### Post by EddySanders on 2008-01-30
works great :) thanks for all the help!

---

