---
title: "No colour all media players"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by LIEFofEeofol on 2007-12-05
Ive had linux for a wile now (ubuntu gutsy).. up untill now when i opened media it was in colour
recently in all media players when i view media its in black and white.....
iv tried reinstalling my nvidia drivers,
my pc's specs are:

intel core 2 duo 1.87ghz
2gigs of ram
160gig hard drive
nvidia 945 chipset

o, and when i click full screen in all media players the screen goes blank (still switched on)
these two things happened at the same time.....

can anyone help?

---

### Post by philinux on 2007-12-05
Try deleting the .vlc .mplayer folders of media players in your home folder. This fixed it for me. 

Next time you fire up mplayer for instance it will recreate its default settings.

---

### Post by LIEFofEeofol on 2007-12-05
i couldnt find these files so i reinstalled vlc and totem/ movie player - no change

---

### Post by asmiller-ke6seh on 2007-12-05
**.vlc** and **.mplayer** are hidden folders - any folder with a "." at the beginning of the name is hidden.

From the graphic directory listing, hold down <Ctrl> and press <H> and your hidden folders will be displayed.

Now, delete the .vlc and .mplayer directories that were hidden in your home directory.

Next time you load vlc or mplayer, these applications will rewrite their configuration file(s). This may resolve your problem with black and white instead of color.

---

### Post by LIEFofEeofol on 2007-12-05
could only fine .vlc, i deleted it no change to movie player or vlc player...

---

### Post by piomboj on 2008-02-26
Hello,
Try using this thread.
Apparently some downloaded media will affect you player and move your color controls.  Just reset to default under preferences and it should work.  This solved my problem.

[http://ubuntuforums.org/showthread.php?t=432197](http://ubuntuforums.org/showthread.php?t=432197)

---

### Post by sayakb on 2008-02-26
Maybe you have the Default Video output set.

For VLC, select the X11 output mode to get the colors. 
Open VLC
Goto Settings -> Preferences
Check the Advanced options checkbox in bottom right side
In left panel, expand Video 
Click Output modules
In the right side, select X11 output mode
Click Save button and restart VLC

I think this should work

---

### Post by LIEFofEeofol on 2008-02-26
Oh, sry i found the solution a while ago...
it was the one Piomboj said that worked,

it is strange thought that totem should affect all other media players....
anyways,
thx all

---

### Post by noland on 2008-03-10
dont know why but the "saturation" was set to zero in preferences, display.  did the trick for me, but dunno what happened...

gutsy 7.10

---

