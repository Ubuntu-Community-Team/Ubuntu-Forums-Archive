---
title: "[help] something wrong when playing video file"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by k66473 on 2008-04-19
I use VLC and Totem to play some video files and following bad issues happen. Please help me to fix them.

1. Some files when viewing with VLC has a green bar on the screen (top header) but they are OK when viewing with Totem. Some files have green bar with both players.

2. When playing movie files, there is a cross line from top right to bottom left of the screen. (hard to see but it is there)

3. I tried to disable screen saver but after several minutes playing movie, the screen turn to blank and I must move the mouse to continue watching the movie.

Hope you can understand what I mean.
Regards.

---

### Post by GuitarRocker2562 on 2008-04-19
Disable compiz by going to system -> preferences -> appearance, click the Visual Effects tab, select none, and click okay, or close or whatever the option is. Did this help? What graphics card are you using? Which edition of ubuntu?

---

### Post by k66473 on 2008-04-20
I am using ubuntu 7.10
my VGA is ATI radeon xpress 1100  (on the laptop acer 5100 serries).

disable compiz ? so all beautiful effect will go away? I have not tried yet but that sound is so sad for me

---

### Post by NightwishFan on 2008-04-20
You only need to disable compiz so we can single out if it is the problem or not. Either way you can continue to use it.

---

### Post by k66473 on 2008-04-20
OK. I turned off Compiz and the problem still remain.
Here is the screenshot of the problem.
Regards.
<a href="http://s198.photobucket.com/albums/aa202/minhtdvn/?action=view&current=Screenshot-1.png" target="_blank"><img src="http://i198.photobucket.com/albums/aa202/minhtdvn/Screenshot-1.png" border="0" alt="Photobucket"></a>

[IMG]http://i198.photobucket.com/albums/aa202/minhtdvn/Screenshot-1.png[/IMG]

---

### Post by NightwishFan on 2008-04-20
In vlc try to set video mode to x11 rather than open gl.

settings -> preferences -> check advanced options -> Video -> Output Modules

---

### Post by k66473 on 2008-04-20
I find out this:
if let the setting of ouput modules is default (or Xvideo..) then above trouble happen.
If I set to openGL or X11 then the screen looks fine but if I swich VLC from full screen mode to normal (by double click) then the system log out automaticly.

---

