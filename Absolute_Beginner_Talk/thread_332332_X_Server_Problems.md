---
title: "X Server Problems"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by Rotodyne on 2007-01-05
Hello, I have just read other threads on problems with X Server but still cannot figure out how to get rid of the error. :confused: 

I am running on a Dell Dimension E510 and want to install Ubuntu, XP is already installed

The error
[IMG]http://img443.imageshack.us/img443/7232/imgp1953be3.jpg[/IMG]

Continued
[IMG]http://img441.imageshack.us/img441/2060/imgp1954iy1.jpg[/IMG]

If you could scroll down in the second picture it would say

(EE) No Devices Detected

Fatal Service Error:
No Screens Found

----------

Here are the steps I took, am I missing something important/obvious?

I downloaded the 6.10 ISO and burned it to a disk
I restarted my computer and booted from CD Drive
Then I tried to install and got the error :(

----------

I already tried using some of the techniques named in another thread such as:

sudo dpkg-reconfigure xserver-xorg

Thanks!

---

### Post by ajmorris on 2007-01-05
what happens if when this happens and it drops back to a shell, if u type 
[PHP]sudo startx[/PHP] ?

---

### Post by Rotodyne on 2007-01-05
> **l337 h4x0r said:**
> what happens if when this happens and it drops back to a shell, if u type 
[PHP]sudo startx[/PHP] ?

I receive the same error message as before,, just in the shell.

---

### Post by ajmorris on 2007-01-05
could u please post some screenshots of ur xorg.conf file?

---

### Post by Rotodyne on 2007-01-05
> **l337 h4x0r said:**
> could u please post some screenshots of ur xorg.conf file?

Would I do this by entering

/etc/X11/xorg.conf

?

Sorry I am very new to this stuff ](*,)

---

### Post by ajmorris on 2007-01-05
if u r and in recovery mode or in a mode with no gui i don't know because the only way i know to take screenshots is by the print screen button in a GUI mode. 
How did you do it before?

---

### Post by Rotodyne on 2007-01-05
> **l337 h4x0r said:**
> if u r and in recovery mode or in a mode with no gui i don't know because the only way i know to take screenshots is by the print screen button in a GUI mode. 
How did you do it before?

they are not screenshots, digital camera pictures :D

---

### Post by ajmorris on 2007-01-05
oh, if it's possible can u take some of ur xorg.conf file? in the shell ( i assume ur in no GUI mode if u can't start xserver) just type 
[PHP]less /etc/X11/xorg.conf[/PHP] It may require sudo but i don't think so.

---

### Post by Rotodyne on 2007-01-05
> **l337 h4x0r said:**
> oh, if it's possible can u take some of ur xorg.conf file? in the shell ( i assume ur in no GUI mode if u can't start xserver) just type 
[PHP]less /etc/X11/xorg.conf[/PHP] It may require sudo but i don't think so.


Yeah i'll get some pics soon

---

### Post by Rotodyne on 2007-01-06
Here they are, the last two pics I didn't post
Sorry some are hard to read :(

[IMG]http://img458.imageshack.us/img458/305/imgp1959ys0.jpg[/IMG]
[IMG]http://img101.imageshack.us/img101/6429/imgp1960zh2.jpg[/IMG]
[IMG]http://img101.imageshack.us/img101/6429/imgp1960zh2.jpg[/IMG]
[IMG]http://img401.imageshack.us/img401/261/imgp1962tb2.jpg[/IMG]
[IMG]http://img119.imageshack.us/img119/9153/imgp1963kf9.jpg[/IMG]
[IMG]http://img154.imageshack.us/img154/9850/imgp1964ug5.jpg[/IMG]

---

### Post by kavon89 on 2007-01-06
Wait a second! Rotodyne and I both have the same GFX card... and the EXACT same problem... see my post in this very section.

[http://www.ubuntuforums.org/showthread.php?t=332371](http://www.ubuntuforums.org/showthread.php?t=332371)

Whats going on with the desktop version of the x300? Please help us!

---

### Post by ajmorris on 2007-01-06
Did you recently install Beryl?

---

