---
title: "I screwed something up bad. HELP"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by Ceta on 2007-02-12
I tried to do the dual monitors thing with the instructions at this link: [http://www.ubuntuforums.org/showthread.php?p=1773710](http://www.ubuntuforums.org/showthread.php?p=1773710)  However, it didnt work, so I changed the last line to FALSE instead of True, which made my TV the primary monitor.  Now I CANT see anything on my tv or my monitor unless I am in safe graphics mode.  But when i go to those settings in safe mode, the dual monitor settings arent in there, so I cant get my display right.  ANY help please??

---

### Post by punx45 on 2007-02-12
while in safe mode, revert to the backup of your xorg.conf so you can get back into regular mode with a regular monitor, then go through the howto again and make sure you didnt miss anything the first time.

(if for some reason you didn't back up a working xorg.conf (there is no good reason!) then in a terminal do ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then ```
sudo /etc/init.d/gdm restart
```   that will get you back to the default so you can use your monitor again

i had to do that plenty of times while trying to add TV out to my nvidia card.

i dont know what kind of problems you are having with the TV out, but one thing I found was that my TV would stay blank unless i set its resolution at 640x480.   some of the guides didnt mention this and set higher resolutions for the TV.   standard NTSC IS 720X480 so that should work too, but i would suggest not going over it (if that is the problem...)

---

### Post by Ceta on 2007-02-12
I'm stupid and didnt make a backup. I typed both those things in a terminal, then rebooted, and nothing changed :(

---

### Post by Ceta on 2007-02-12
When I type sudo /etc/init.d/gdm restart it says starting gnome display manager... fail

---

### Post by ndefontenay on 2007-02-12
What about simply ```
dpkg-reconfigure xserver-xorg
``` without phigh parameter?

---

