---
title: "3 (or more) button mouse - G5"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by General_Ts0 on 2007-03-14
First week on Ubuntu.  Trying to figure out how to play games and then I'll be more patient with it (not having to switch back to Windows).

Meanwhile, even in browsing I can't figure out what I need to do to make it so that I can use my 3rd mouse button (thumb).  Even if/when I get gaming on (FPS please!) I won't have my thumb button.  Preferences > Mouse doesn't give an option to enable/configure . 

Wheel works fine as does the accelerate/decelerate buttons.

---

### Post by oilchangeguy on 2007-03-14
in the upper right of the page there is a search box. i typed in 3 button mouse, clicked go, and there's 26 posts on the subject. one of them should contain your answer.

---

### Post by kelbizzle on 2007-03-14
just today I thought. I try to get my thumb buttons 8 9 to work with firefox.  I have an intellimouse 2.0 and just counted up the buttons of the mouse and just changed the lines in my xorg.conf. 
```
    Option          "ButtonMapping" "1 2 3 6 7 8 9"
    Option         "ZAxisMapping" "4 5"
#   Option         "Emulate3Buttons" "true"
```

4 and 5 are usually the scroll. I know theres a command you can use to find out which button is pressed.

---

### Post by General_Ts0 on 2007-03-15
when I try to open xorg.conf thru Nautilus, I don't have permissions to change it, only root does (and have read all about [Ubuntu's view on root]("https://help.ubuntu.com/community/RootSudo")).  If I drop to a console and try to 'cd' to /etc/X11, it says X11 doesn't exist (checked caps of 'x') so I can't edit the xorg.conf file to include these suggestions.  So therefore I can't 'sudo' thru terminal in order to 'pico' xorg.conf and add these lines.

username@username-desktop:~$ **cd /etc**
username@username-desktop:/etc$ **cd /X11**
*results in* bash: cd:  /X11:  No such file or directory

But it's freakin there in Nautilus and even when I 'ls' it's there in purple.

What am I missing ?

---

### Post by kelbizzle on 2007-03-15
man you should be able to do it. 
```
gksudo gedit /etc/X11/xorg.conf
```
or 
```
sudo nano /etc/X11/xorg.conf
``` to edit it in the console window Ctrl+o to save it and ctrl+x to quit using nano

---

### Post by omghax on 2007-03-15
Your first line was good, but your second line was trying to cd into /X11, not /etc/X11.

---

### Post by General_Ts0 on 2007-03-15
> **omghax said:**
> Your first line was good, but your second line was trying to cd into /X11, not /etc/X11.

sweet, that did it.  I didn't know you had to use a fully distinguished name.  I figured like MS-DOS that a relative name would work.  Was able to get in, apply the changes [per this forum post [first section]]("http://www.ubuntuforums.org/showthread.php?t=316441&highlight=howto+mouse") and I'm golden.

---

