---
title: "How do I change taskbar icons?"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by thelocust on 2007-01-27
[SIZE=2][B]

Ok I installed KDE crystal dimaond icon set and it looks great. Only my icons dont mach up with what shows on the task bar and the pop-ups on my application panel. I looked alover and replaced a bunch of the old icons with the ones I want (mainly firefox and thunderbird) and nothing changes. I need to know were KDE is pulling these icons from so that I can change them. Thanks.


[/B][/SIZE]

---

### Post by ComplexNumber on 2007-01-27
> **thelocust said:**
> [SIZE=2][B]

Ok I installed KDE crystal dimaond icon set and it looks great. Only my icons dont mach up with what shows on the task bar and the pop-ups on my application panel. I looked alover and replaced a bunch of the old icons with the ones I want (mainly firefox and thunderbird) and nothing changes. I need to know were KDE is pulling these icons from so that I can change them. Thanks.


[/B][/SIZE]
if you've just changed your theme, kde seems to need a restart of the xserver, so logout and then log back in again.

the icons are in /usr/share/icons, /usr/share/pixmaps, and /home/<your-username>/.kde/share/icons(for icons stored in your home directory).

---

### Post by thelocust on 2007-01-27
[B]
My icon theme has been install for some time now so theres nothing wrong with that and the only folder I was missing was the pixmap folder. But now have have replaced all the icons in all 3 folder with the icons I want and its still not working. I put some sceen shots to clear up any confusion about my question. 

Screenshot1 is were the pop-up does not match my icon

screenshot2 is were the taskbar icon does not match

and screenshots 3&4 are were the taskbar has a red X for an icon.

Can anyone help me with this, I think I might have to edit some config files or something. Thanks.


[/B]

---

### Post by closetpirate on 2007-02-03
This is an older post but I thought someone might have a followup. I believe I have the same question. I have used the gimp to illustrate further what I am trying to find out. Basically, I have changed the icons located in the give places but still have the icons for iceweasel as illustrated in the screenshots.

then again.... maybe I should just start a new thread

---

### Post by ComplexNumber on 2007-02-03
> **closetpirate said:**
> This is an older post but I thought someone might have a followup. I believe I have the same question. I have used the gimp to illustrate further what I am trying to find out. Basically, I have changed the icons located in the give places but still have the icons for iceweasel as illustrated in the screenshots.

then again.... maybe I should just start a new thread
its the same solution for you. i always found that kde needed to have to refresh the xserver for some  theme changes to take effect - for example, the background of various icons on the panel, icons in the system tray,etc.

---

### Post by randiroo76073 on 2007-02-03
Simular prob & refreshing does not change it one bit, even reboot does nothing to change it.

---

### Post by closetpirate on 2007-02-04
I did read the previous reply but even restarting of X didn't do it. I posted the problem at KDE forums but the only response I have gotten is that the files are broken up into 16x16, 22x22. Well that is pretty obvious but I still can't find out where that particular graphic is coming from. I have deleted all the traces I can't find of that old blue iceweasel graphic but it isn't gone. I am about to give up.

thanks anyways
Joel

ps: if i do find the solution I will post it here because I apparently am not the only one with the same problem

---

### Post by closetpirate on 2007-02-04
okay.....after a while I found that the icons were in the program file themselves at /usr/lib/iceweasel/chrome/icons/default/default.xpm
I would imagine that there is an equivalent for other applications

hope my findings help
here is the difference

---

### Post by randiroo76073 on 2007-02-04
Thanks for update Closetpirate, I think that if you replace icons in a theme[naming them same as originals] then you can have permanent change, lota work tho.

---

### Post by thelocust on 2007-02-04
[B]
Wow thanks alot I would have never found that.

[/B]

---

### Post by flamacue on 2007-12-15
Thanks fellas, you helped me solve a problem.  See

_[http://ubuntuforums.org/showthread.php?p=3956962#post3956962](http://ubuntuforums.org/showthread.php?p=3956962#post3956962)_

for details.

---

